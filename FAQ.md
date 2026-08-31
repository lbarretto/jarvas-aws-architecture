# ❓ FAQ — Perguntas Frequentes

### ☁️ Startup Jarva's — Plataforma SaaS de Gestão de Documentos com IA

Este documento reúne as principais dúvidas sobre a arquitetura, funcionamento, segurança, custos e evolução da **Startup Jarva's**.

As respostas refletem as decisões e o escopo definidos para a **Fase 01** do projeto. Quando determinado recurso ainda não foi implementado ou formalizado, isso é indicado explicitamente.

---

## 📌 Índice

* [🎯 Sobre o projeto](#-sobre-o-projeto)
* [🏗️ Arquitetura e funcionamento](#️-arquitetura-e-funcionamento)
* [🔒 Segurança](#-segurança)
* [🗃️ Armazenamento e retenção](#️-armazenamento-e-retenção)
* [📈 Escalabilidade e resiliência](#-escalabilidade-e-resiliência)
* [💰 Custos](#-custos)
* [🧱 Infraestrutura como Código](#-infraestrutura-como-código)
* [⚠️ Limitações da Fase 01](#️-limitações-da-fase-01)
* [🚀 Evolução para a Fase 02](#-evolução-para-a-fase-02)

---

## 🎯 Sobre o projeto

### O que é a Startup Jarva's?

A Startup Jarva's é uma plataforma SaaS voltada para **gestão e armazenamento de documentos utilizados como insumo para soluções de Inteligência Artificial**.

O cenário prevê aproximadamente **50 mil novos arquivos por mês**, principalmente PDFs e imagens, podendo chegar a milhões de documentos ao longo dos anos.

O diferencial do problema é que esses documentos possuem valor histórico e, na operação normal, **não devem ser excluídos**, pois podem servir como base para a evolução futura dos modelos de IA.

### Qual problema a arquitetura precisa resolver?

A arquitetura foi projetada para lidar simultaneamente com quatro necessidades principais:

* crescimento contínuo do volume de documentos;
* isolamento dos dados entre diferentes clientes;
* retenção dos documentos por longos períodos;
* controle do custo de armazenamento.

A proposta, portanto, não é simplesmente guardar arquivos, mas criar uma infraestrutura capaz de preservar esse histórico de dados de forma segura, escalável e economicamente sustentável.

### O projeto realmente implementa Inteligência Artificial?

**Não na Fase 01.**

A Fase 01 concentra-se na **infraestrutura responsável por receber, proteger, armazenar, organizar e disponibilizar os documentos** que poderão alimentar futuras soluções de IA.

A arquitetura foi construída para preparar a base de dados necessária para essa evolução, mas o processamento ou treinamento de modelos de IA não faz parte do escopo apresentado nesta etapa.

### Por que esse projeto é relevante?

Porque o crescimento da quantidade de dados transforma o armazenamento em uma preocupação estratégica.

À medida que a empresa recebe dezenas de milhares de documentos por mês, esses dados deixam de ser apenas arquivos armazenados e passam a representar um histórico que poderá gerar valor para a evolução dos modelos de IA.

---

# 🏗️ Arquitetura e funcionamento

### Por que a arquitetura utiliza Serverless?

Porque o cenário prevê crescimento contínuo sem exigir que a equipe mantenha e dimensione servidores manualmente.

A solução utiliza serviços gerenciados como:

**Amazon Cognito → API Gateway → Lambda → DynamoDB + S3**

Esse modelo permite separar responsabilidades e acompanhar a demanda utilizando serviços gerenciados pela AWS.

### Como funciona o fluxo de uma operação?

O fluxo principal é:

1. O usuário realiza login pelo **Amazon Cognito**.
2. O Cognito fornece um token de autenticação.
3. A requisição chega ao **Amazon API Gateway**.
4. O API Gateway encaminha a requisição autorizada para o **AWS Lambda**.
5. O Lambda consulta o **DynamoDB** para validar a propriedade do documento.
6. O Lambda gera uma **URL pré-assinada**.
7. O cliente realiza o upload ou download diretamente no **Amazon S3**.

### Por que o arquivo não passa pelo Lambda?

Porque o Lambda não precisa atuar como intermediário na transferência do arquivo.

Em vez disso, ele apenas valida a operação e gera uma URL temporária. A transferência ocorre diretamente entre o cliente e o Amazon S3.

Isso reduz o trabalho realizado pela função e evita utilizar a camada de processamento para transportar arquivos potencialmente grandes.

### O que é uma URL pré-assinada?

É uma URL temporária que permite realizar uma operação específica em um objeto do Amazon S3.

Ela permite que o cliente faça upload ou download sem precisar receber credenciais permanentes da AWS e sem tornar o bucket público.

### Por que usar DynamoDB?

Porque o caso de uso apresentado possui uma estrutura simples de metadados, principalmente relacionada à propriedade dos documentos.

O DynamoDB permite armazenar essas informações com escalabilidade automática e sem a necessidade de administrar um servidor de banco de dados tradicional.

### Por que não utilizar RDS?

Porque o problema apresentado não exige, na Fase 01, a estrutura relacional e a administração adicional de um banco como o RDS.

O DynamoDB atende ao modelo de dados proposto com uma abordagem mais alinhada ao restante da arquitetura serverless.

---

# 🔒 Segurança

### Como um cliente é impedido de acessar o documento de outro cliente?

A aplicação associa cada documento ao seu proprietário por meio dos metadados armazenados no DynamoDB.

Antes de gerar uma URL pré-assinada, o Lambda verifica se o usuário autenticado possui autorização para acessar aquele documento.

Além disso, o bucket S3 permanece privado.

### O bucket S3 é público?

**Não.**

O `infrastructure.yaml` configura o **Block Public Access** no bucket, impedindo acesso público por ACLs ou políticas públicas.

### Como funciona a autenticação?

A autenticação é realizada pelo **Amazon Cognito**.

O Cognito gerencia os usuários e fornece os tokens utilizados para autenticação das requisições.

O API Gateway utiliza essa autenticação antes que a chamada chegue à lógica de negócio.

### Existe MFA?

Na Fase 01, o MFA está configurado como **OFF**.

A utilização de MFA é considerada uma possível evolução para uma etapa posterior.

### Os dados são criptografados?

Sim.

Os objetos armazenados no S3 utilizam **SSE-S3**, enquanto o DynamoDB também possui criptografia habilitada.

O uso de **AWS KMS** para ampliar o controle sobre as chaves criptográficas está previsto como evolução da Fase 02.

### O que significa Least Privilege na arquitetura?

Significa conceder a cada componente somente as permissões necessárias para executar sua função.

Por exemplo, a role da Lambda possui permissões direcionadas ao DynamoDB, S3 e CloudWatch utilizados pela aplicação, evitando permissões genéricas desnecessárias.

### Como as ações na infraestrutura podem ser auditadas?

O projeto utiliza o **AWS CloudTrail** para registrar ações realizadas na conta e nos serviços AWS.

O **Amazon CloudWatch** complementa essa estratégia com observabilidade operacional.

---

# 🗃️ Armazenamento e retenção

### Por que os documentos não são excluídos?

Porque o cenário considera esses documentos como parte do histórico que poderá ser utilizado na evolução futura dos modelos de IA.

O crescimento desse histórico é, portanto, uma característica do próprio negócio.

### Como impedir exclusões ou alterações durante o período de retenção?

O Amazon S3 utiliza **Versioning** e **S3 Object Lock**.

O Object Lock aplica uma política de retenção aos objetos, protegendo-os contra exclusão ou alteração durante o período configurado.

Na configuração atual do template, o período padrão é de **3650 dias**, aproximadamente 10 anos.

### Os documentos ficam sempre no armazenamento mais caro?

Não.

A arquitetura utiliza o ciclo de vida do S3 para reduzir o custo conforme os documentos envelhecem.

Documentos recentes permanecem em uma camada adequada para acesso frequente, enquanto documentos históricos são direcionados para **S3 Glacier Deep Archive**.

### Quando os documentos vão para o Glacier Deep Archive?

A política definida no projeto prevê a transição após **365 dias**.

A finalidade é reduzir o custo de armazenamento dos documentos antigos que continuam precisando ser preservados, mas possuem menor frequência de acesso.

### O que acontece se um documento antigo precisar ser acessado?

O documento continua armazenado, mas o acesso a dados arquivados pode envolver características e custos diferentes daqueles de uma classe de armazenamento de acesso frequente.

Por isso, o comportamento de acesso aos documentos históricos deve ser considerado na análise de custos.

### Existe backup adicional?

Na Fase 01, não foi implementado um mecanismo adicional de backup além dos recursos de durabilidade e recuperação disponibilizados pelos serviços utilizados.

Uma estratégia de backup mais abrangente é considerada uma possibilidade de evolução conforme aumente a criticidade da operação.

---

# 📈 Escalabilidade e resiliência

### O que acontece se o volume de documentos aumentar muito?

A arquitetura utiliza componentes serverless e gerenciados, como:

* API Gateway;
* Lambda;
* DynamoDB;
* S3.

Esses serviços foram escolhidos justamente para permitir crescimento sem depender de uma única máquina ou de provisionamento manual constante.

### E se houver um pico repentino de uploads?

A arquitetura foi desenhada para suportar variações de demanda por meio do modelo serverless.

Entretanto, o comportamento real continua condicionado aos limites e quotas dos serviços AWS utilizados.

### Existe algum ponto único de falha?

Não existe uma única máquina responsável pela aplicação inteira.

A solução utiliza serviços gerenciados pela AWS e distribui responsabilidades entre diferentes componentes.

Isso reduz a dependência de uma única instância administrada pela equipe.

### A arquitetura é imune a falhas?

**Não.**

Serverless e serviços gerenciados não significam que a aplicação não possa falhar.

Problemas de lógica, permissões incorretas, configurações inadequadas ou indisponibilidade de serviços ainda precisam ser considerados.

A arquitetura busca reduzir determinados pontos de falha e melhorar a capacidade de observação e recuperação, mas não elimina todos os riscos.

### Existem metas de RTO e RPO?

Ainda **não foram formalizadas na Fase 01**.

Esse é um dos pontos identificados para evolução futura da arquitetura.

---

# 💰 Custos

### Qual é o custo estimado da arquitetura?

A estimativa apresentada é de:

* **US$ 143,54/mês** em custos recorrentes;
* **US$ 33,00** em custos iniciais;
* **US$ 1.755,48** projetados para 12 meses.

Esses valores são estimativas baseadas nas premissas documentadas para o cenário.

### Onde está concentrado o custo?

A maior parte do custo está relacionada ao armazenamento e à transferência dos documentos.

Os principais componentes estimados são:

| Serviço                       | Custo mensal estimado |
| ----------------------------- | --------------------: |
| Amazon S3 Intelligent-Tiering |             US$ 65,63 |
| Transferência de dados        |             US$ 61,44 |
| S3 Glacier Deep Archive       |              US$ 8,42 |
| Amazon CloudWatch             |              US$ 6,18 |
| Demais serviços               |         < 1% do total |

### Por que armazenamento e transferência custam mais do que Lambda?

Porque o cenário possui um volume elevado de documentos e operações de leitura.

A arquitetura foi desenhada justamente para que o armazenamento acompanhe o ciclo de vida dos dados e para evitar manter todo o histórico em classes mais caras.

### O custo aumenta com o crescimento da empresa?

**Sim.**

Como os documentos não são descartados como parte da operação normal, o volume armazenado cresce continuamente.

O objetivo do S3 Lifecycle e do Glacier Deep Archive não é impedir esse crescimento, mas **reduzir seu impacto financeiro**.

### A estimativa de custo é definitiva?

Não.

Os valores são uma projeção baseada em uma série de premissas, como volume de documentos, tamanho médio dos objetos, quantidade de leituras e região AWS.

O custo real pode variar conforme o comportamento da aplicação.

### Por que foi escolhida a região N. Virginia?

A estimativa utilizou a região **US East (N. Virginia)** como referência de preço.

Em uma implantação real, a região poderia ser reavaliada considerando requisitos de latência, localização dos clientes e custo.

### Por que o S3 Transfer Acceleration não foi habilitado?

Porque, na Fase 01, o cenário não demonstra necessidade suficiente para justificar seu custo adicional.

A funcionalidade foi mantida como uma possibilidade para uma futura expansão geográfica da plataforma.

---

# 🧱 Infraestrutura como Código

### Por que utilizar CloudFormation?

Porque a infraestrutura deixa de depender de configuração manual.

O `infrastructure.yaml` descreve os recursos necessários para criar a arquitetura, permitindo maior padronização e reprodutibilidade entre ambientes.

### É possível utilizar o mesmo template em ambientes diferentes?

Sim.

O template possui parâmetros como:

* `dev`;
* `hml`;
* `prod`.

Também existem parâmetros para controlar aspectos como retenção, logs, nome do projeto e Transfer Acceleration.

### Existem credenciais dentro do template?

Não.

O template não foi projetado para armazenar credenciais diretamente.

Além disso, utiliza restrições de parâmetros para impedir determinados valores inválidos antes da criação da stack.

### O que acontece se um recurso precisar ser recriado?

Alguns recursos importantes, como o bucket S3 e a tabela DynamoDB, possuem políticas de retenção definidas no CloudFormation.

Isso ajuda a evitar que alterações na infraestrutura provoquem perda automática dos dados armazenados.

---

# ⚠️ Limitações da Fase 01

### O projeto está pronto para produção?

**Ainda não completamente.**

A Fase 01 representa a arquitetura e a infraestrutura propostas para o MVP.

O próprio template ainda possui elementos que precisam ser substituídos ou ajustados para uma implantação real, como:

* código definitivo da função Lambda;
* URL de callback real do Cognito;
* configuração completa do ambiente de aplicação;
* demais componentes de CI/CD necessários para uma implantação operacional.

### Por que a Lambda possui um código placeholder?

Porque o objetivo principal do template apresentado é representar a **infraestrutura da solução**.

O código atualmente fornecido pela Lambda é um placeholder que deve ser substituído pelo artefato real da aplicação antes de uma implantação definitiva.

### O que ainda não está formalizado?

Entre os pontos identificados para evolução estão:

* metas de RTO/RPO;
* estratégia de backup adicional;
* mecanismos mais avançados de segurança;
* controles adicionais de dados sensíveis;
* evolução da experiência para usuários geograficamente distantes.

### A retenção permanente pode gerar um problema com a LGPD?

Sim.

Existe uma tensão entre a exigência de negócio de preservar os documentos e situações em que um titular possa solicitar a exclusão de seus dados.

Esse ponto precisa ser tratado de maneira específica em uma evolução futura da solução, com uma política de retenção e exclusão compatível com os requisitos legais aplicáveis.

---

# 🚀 Evolução para a Fase 02

### O que está planejado para a Fase 02?

A Fase 02 não substitui a arquitetura existente.

Ela parte da base construída na Fase 01 e adiciona recursos conforme aumentam o volume de dados, a criticidade da operação e a necessidade de governança.

Entre as evoluções avaliadas estão:

| Recurso                               | Objetivo                                                         |
| ------------------------------------- | ---------------------------------------------------------------- |
| AWS KMS                               | Maior controle sobre chaves criptográficas                       |
| AWS Secrets Manager                   | Gerenciamento seguro de segredos                                 |
| Amazon Macie                          | Identificação de dados sensíveis no S3                           |
| S3 Transfer Acceleration              | Melhorar transferências em cenários geograficamente distribuídos |
| Estratégias adicionais de resiliência | Aumentar a maturidade operacional                                |
| Controles adicionais de segurança     | Fortalecer proteção e governança                                 |

### Por que não colocar todos esses serviços desde o início?

Porque adicionar serviços não significa automaticamente criar uma arquitetura melhor.

A estratégia adotada é incorporar uma tecnologia quando existe uma **necessidade concreta** que justifique sua complexidade, custo e operação.

Isso evita transformar a arquitetura em um conjunto de serviços utilizados apenas por excesso de zelo ou por tendência tecnológica.

---

## 🧭 Em uma frase, qual é a ideia central da arquitetura?

> **Construir uma infraestrutura capaz de preservar o crescimento contínuo dos dados da Startup Jarva's sem comprometer segurança, escalabilidade e sustentabilidade financeira.**

---

### 📚 Documentação relacionada

* [`README.md`](./README.md) — visão completa do projeto e decisões arquiteturais.
* [`README.en.md`](./README.en.md) — versão em inglês.
* [`Precificação Serviços AWS - Startup Jarva's.md`](./Precificação%20Serviços%20AWS%20-%20Startup%20Jarva's.md) — premissas e estimativas de custos.
* [`infrastructure.yaml`](./infrastructure.yaml) — infraestrutura como código em AWS CloudFormation.
