# ❓ FAQ — Perguntas e Respostas do Projeto

[#-faq--perguntas-e-respostas-do-projeto](#-faq--perguntas-e-respostas-do-projeto)

### ☁️ Startup Jarva's — Plataforma SaaS de Gestão de Documentos com IA

Este documento reúne as principais perguntas que podem surgir durante a apresentação e defesa do projeto, organizadas por tema, com respostas diretas baseadas nas decisões documentadas no [README principal](./README.md).

> 💡 As respostas refletem as decisões da **Fase 01** do projeto. Pontos ainda não formalizados (como metas de RTO/RPO) são tratados de forma transparente como parte da evolução prevista na **Fase 02**.

---

## 📌 Sumário

- [🏗️ Arquitetura e Fluxo](#️-arquitetura-e-fluxo)
- [🔒 Segurança](#-segurança)
- [📈 Escalabilidade e Resiliência](#-escalabilidade-e-resiliência)
- [🗃️ Retenção e Durabilidade](#️-retenção-e-durabilidade)
- [💰 Custos](#-custos)
- [🧭 WAF e CAF](#-waf-e-caf)
- [🧱 Infraestrutura como Código](#-infraestrutura-como-código)
- [🚀 Evolução (Fase 02)](#-evolução-fase-02)
- [🛟 Como responder quando não souber algo](#-como-responder-quando-não-souber-algo)

---

## 🏗️ Arquitetura e Fluxo

[#️-arquitetura-e-fluxo](#️-arquitetura-e-fluxo)

**Por que a arquitetura é serverless em vez de usar servidores fixos (EC2)?**
Porque o cenário exige acompanhar um crescimento contínuo (~50 mil arquivos/mês) sem que a equipe precise dimensionar servidores manualmente. Serviços gerenciados como Lambda, API Gateway, DynamoDB e S3 escalam automaticamente e cobram pelo uso real, além de reduzir pontos únicos de falha.

**Como funciona o fluxo de uma requisição, do login ao armazenamento do arquivo?**
1. O usuário loga via Amazon Cognito e recebe um token JWT.
2. A requisição vai para o API Gateway, que valida o token.
3. O AWS Lambda processa a lógica de negócio e consulta o DynamoDB para validar propriedade do documento.
4. O Lambda gera uma URL pré-assinada temporária.
5. O upload/download acontece direto no S3 usando essa URL, sem passar pelo Lambda/API Gateway.

**Por que o upload/download não passa pelo Lambda?**
Para não sobrecarregar a função com transferência de arquivos grandes e evitar custo/tempo de execução desnecessários. A URL pré-assinada garante acesso seguro e temporário diretamente ao S3.

**O que é uma URL pré-assinada e por que ela é segura?**
É um link temporário, gerado pelo backend, que concede permissão para uma operação específica (ex: um único PUT ou GET) em um objeto específico, por um tempo limitado — sem tornar o bucket público nem expor credenciais permanentes.

**Por que Cognito e não uma autenticação própria (custom)?**
Porque é um serviço gerenciado que já lida com emissão de token JWT, MFA opcional e gerenciamento de usuários, evitando reinventar uma parte crítica do sistema.

**Por que DynamoDB e não um banco relacional (RDS)?**
Porque o caso de uso é simples (metadados chave-valor: quem é dono de qual documento) e precisa escalar automaticamente sem administração manual, o que o DynamoDB oferece nativamente.

**Por que S3 Intelligent-Tiering em vez de S3 Standard?**
Porque move automaticamente os objetos entre camadas de acesso com base no padrão real de uso, sem precisarmos configurar regras manuais — otimizando custo desde o início.

[⬆️ Voltar ao topo](#-sumário)

---

## 🔒 Segurança

[#-segurança](#-segurança)

**Como vocês garantem que um cliente não acesse os documentos de outro (multi-tenant)?**
Cada documento tem metadados no DynamoDB associando o arquivo ao seu dono. Antes de gerar qualquer URL pré-assinada, o Lambda valida no DynamoDB se o usuário autenticado é o proprietário. O bucket S3 é privado, sem acesso público.

**Como funciona a autenticação?**
Pelo Amazon Cognito, que emite tokens JWT validados pelo API Gateway antes de qualquer chamada chegar à lógica de negócio.

**Os dados são criptografados?**
Sim, em repouso, com criptografia server-side padrão do S3 (SSE-S3). O AWS KMS está previsto como evolução (Fase 02) para maior controle sobre chaves.

**O que é "least privilege" e onde aparece na arquitetura?**
É dar a cada componente só a permissão mínima necessária pra sua função — por exemplo, a role do Lambda tem permissão específica apenas para o bucket S3 e a tabela DynamoDB da aplicação, controlado via AWS IAM.

**Por que Macie e Secrets Manager não entraram já na Fase 01?**
Porque não havia necessidade concreta que justificasse a complexidade e o custo adicional nesse momento. O princípio adotado foi: só incorporar um serviço quando o cenário realmente exigir.

**Se houver uma tentativa de acesso indevido, como vocês descobririam?**
O AWS CloudTrail registra as chamadas de API feitas na conta, permitindo rastrear quem fez o quê e quando, combinado com alarmes no CloudWatch para identificar padrões anômalos.

**Como a retenção permanente se relaciona com o direito ao esquecimento da LGPD?**
É uma tensão real: a política de negócio é reter tudo para uso futuro em IA, o que pode conflitar com pedidos de exclusão sob a LGPD. É um ponto de evolução necessário — talvez uma exceção controlada para exclusão sob demanda, sem comprometer o restante do histórico.

[⬆️ Voltar ao topo](#-sumário)

---

## 📈 Escalabilidade e Resiliência

[#-escalabilidade-e-resiliência](#-escalabilidade-e-resiliência)

**O que acontece se o volume crescer 10x?**
Por ser 100% serverless, Lambda, API Gateway, DynamoDB e S3 escalam automaticamente conforme a demanda, sem provisionamento manual.

**Existe algum ponto único de falha?**
Não no sentido de servidor administrado pela equipe — todos os componentes principais são gerenciados pela AWS, com alta disponibilidade nativa entre zonas de disponibilidade.

**O que acontece se um componente falhar?**
Não há uma única instância responsável por tudo. O CloudWatch monitora o comportamento operacional e o CloudTrail audita as ações, permitindo identificar e investigar problemas rapidamente.

**O que aconteceria num pico repentino de uploads?**
O API Gateway e o Lambda escalam automaticamente para atender picos, dentro dos limites de concorrência da conta (ajustáveis via suporte AWS se necessário).

[⬆️ Voltar ao topo](#-sumário)

---

## 🗃️ Retenção e Durabilidade

[#️-retenção-e-durabilidade](#️-retenção-e-durabilidade)

**Por que os arquivos nunca podem ser deletados?**
Porque representam a base histórica usada para treinar futuros modelos de IA da empresa — um requisito estratégico de negócio, não apenas técnico.

**O que impede a exclusão ou alteração acidental de um documento?**
O S3 Object Lock, configurado com um período de retenção, impede exclusão/alteração mesmo diante de erro humano ou de uma credencial comprometida.

**Qual o RTO/RPO definido para recuperação de desastres?**
Não formalizamos metas de RTO/RPO na Fase 01 — é um ponto identificado como necessário evoluir na Fase 02. Hoje contamos com a durabilidade nativa do S3 e a resiliência multi-AZ dos serviços gerenciados.

**Existe backup adicional além da durabilidade nativa do S3?**
Não implementamos backup adicional na Fase 01 além da durabilidade e replicação nativas do S3 e DynamoDB — é um ponto de evolução conforme a criticidade da operação aumente.

[⬆️ Voltar ao topo](#-sumário)

---

## 💰 Custos

[#-custos](#-custos)

**Qual o custo mensal estimado da solução?**
US$ 143,54/mês recorrente, com custo inicial de US$ 33,00 e projeção de US$ 1.755,48 em 12 meses — o que dá cerca de **US$ 0,0029 por documento processado**.

**Onde está concentrado o custo?**
Em armazenamento e transferência de dados, não em processamento:
- 🗄️ S3 Intelligent-Tiering: ~US$ 65,63/mês
- 🌐 Transferência de dados: ~US$ 61,44/mês
- ❄️ S3 Glacier Deep Archive: ~US$ 8,42/mês
- 📊 CloudWatch: ~US$ 6,18/mês
- ⚙️ Demais serviços (Lambda, API Gateway, DynamoDB, Cognito): menos de 1% do total

**Como a estimativa foi calculada?**
Usando a AWS Pricing Calculator, na região Leste dos EUA (N. da Virgínia), com premissas de volume e padrão de acesso documentadas no [arquivo de precificação](./Precifica%C3%A7%C3%A3o%20Servi%C3%A7os%20AWS%20-%20Startup%20Jarva's.md) do repositório.

**Por que essa região e não São Paulo?**
A região N. Virginia geralmente tem preços mais baixos que São Paulo para a maioria dos serviços AWS. Numa implementação real, se a latência para clientes brasileiros for um requisito, a região poderia ser reavaliada, impactando o custo.

**Por que o S3 Transfer Acceleration não foi usado na Fase 01?**
Porque aumentaria significativamente o custo, e o cenário atual não comprova necessidade de otimizar transferência para clientes geograficamente distantes. Ficou reservado como possível evolução de Fase 02.

**Esse custo cresce com o tempo, já que nada é deletado?**
Sim, o volume total armazenado cresce mês a mês, mas o S3 Lifecycle move dados antigos para o Glacier Deep Archive (muito mais barato), suavizando bastante o crescimento do custo em comparação a manter tudo em acesso frequente.

**Os serviços cobram por volume armazenado ou também por operação (request)?**
Os dois: além do custo por GB/mês, cada operação tem custo próprio (PUT/GET no S3, invocações do Lambda, requisições do API Gateway, leitura/escrita do DynamoDB). Nesse volume, o processamento é leve comparado ao armazenamento/transferência.

**Existe algum custo "escondido" nesse tipo de arquitetura?**
Alguns exemplos: taxa de exclusão antecipada do Glacier Deep Archive (retenção mínima de 180 dias), custo de recuperação (retrieval) caso um documento arquivado precise ser acessado, e custo de armazenamento de logs do CloudWatch se não houver política de expiração configurada.

**Como o AWS Budgets e o Cost Explorer ajudam no controle de custo?**
O Budgets permite definir limites e criar alertas automáticos quando o gasto se aproxima do previsto (proativo). O Cost Explorer analisa padrões históricos de gasto e ajuda a identificar tendências e oportunidades de otimização (analítico).

**US$ 0,0029 por documento é caro ou barato para esse negócio?**
É um custo baixo considerando o valor estratégico do dado — cada documento não é só um custo de armazenamento, é matéria-prima para o treinamento de modelos de IA futuros da empresa.

[⬆️ Voltar ao topo](#-sumário)

---

## 🧭 WAF e CAF

[#-waf-e-caf](#-waf-e-caf)

**Qual a diferença entre o AWS CAF e o Well-Architected Framework?**
O CAF conecta a arquitetura às necessidades de negócio, segurança, operação e gestão de forma ampla. O WAF oferece princípios técnicos específicos para avaliar se a arquitetura é segura, confiável, eficiente e sustentável.

**Como a solução se relaciona com os pilares do WAF?**

| Pilar | Como contribui |
|---|---|
| 🔐 Segurança | Cognito, IAM, API Gateway, Lambda, URLs pré-assinadas, criptografia server-side |
| 🛡️ Confiabilidade | Serviços gerenciados, S3 Lifecycle/Object Lock, CloudWatch, IaC |
| ⚡ Eficiência de performance | Arquitetura serverless que acompanha a demanda automaticamente |
| 💰 Otimização de custos | S3 Lifecycle, evita serviços sem necessidade concreta |
| 📊 Excelência operacional | CloudWatch, CloudTrail, CloudFormation |

[⬆️ Voltar ao topo](#-sumário)

---

## 🧱 Infraestrutura como Código

[#-infraestrutura-como-código](#-infraestrutura-como-código)

**Por que usar Infraestrutura como Código?**
Para que a infraestrutura seja reproduzível, consistente e versionável, reduzindo dependência de configuração manual e erro humano.

**Por que CloudFormation e não Terraform?**
Por ser nativo da AWS, integrar diretamente com IAM, e ter sido a ferramenta trabalhada durante a preparação da certificação Cloud Practitioner da equipe.

**Quais recursos o template provisiona?**
Os principais componentes da arquitetura: Cognito, API Gateway, Lambda, DynamoDB, o bucket S3 com suas configurações de Lifecycle e Object Lock, e as roles de IAM associadas — disponível em [`infrastructure.yaml`](./infrastructure.yaml).

[⬆️ Voltar ao topo](#-sumário)

---

## 🚀 Evolução (Fase 02)

[#-evolução-fase-02](#-evolução-fase-02)

**O que faltaria para essa solução estar pronta para produção?**
Definir metas formais de RTO/RPO, avaliar a adoção de KMS/Secrets Manager/Macie conforme a sensibilidade real dos dados, e formalizar um plano de continuidade de negócio — todos já mapeados como parte da Fase 02.

**Em que cenário o S3 Transfer Acceleration passaria a fazer sentido?**
Numa expansão internacional real, com clientes geograficamente distantes do bucket, aumento significativo do tamanho dos arquivos, ou evidência (métrica/feedback) de degradação na experiência de upload/download por distância geográfica.

**Por que KMS, Secrets Manager e Macie ficaram para depois?**
Porque não havia necessidade concreta que justificasse a complexidade e o custo adicional agora. A adoção depende do crescimento da sensibilidade dos dados e da maturidade operacional da plataforma.

[⬆️ Voltar ao topo](#-sumário)

---

**☁️ Startup Jarva's** — Plataforma SaaS de Gestão de Documentos com IA
[📄 Ver README principal](./README.md)
