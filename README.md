# ☁️ Startup Jarva's - Plataforma SaaS de Gestão de Documentos com IA

<!-- CAPA DO PROJETO -->
<p align="center">
  <img src="./assets/cover.png" alt="Capa do projeto Startup Jarva's">
</p>

> **Projeto desenvolvido como parte do desafio proposto pela Escola da Nuvem para aplicação prática dos conhecimentos em AWS Cloud e arquitetura de soluções em nuvem.**

---

## 📌 Sumário

- [1. Contextualização do TCC](#1-contextualização-do-tcc)
  - [O que é o projeto?](#o-que-é-o-projeto)
  - [Por que acreditamos que seja um tema relevante?](#por-que-acreditamos-que-seja-um-tema-relevante)
- [2. Contextualização do Projeto](#2-contextualização-do-projeto)
- [3. Problema a ser resolvido e impacto no negócio](#3-problema-a-ser-resolvido-e-impacto-no-negócio)
  - [Segurança e isolamento dos dados](#segurança-e-isolamento-dos-dados)
  - [Retenção dos documentos](#retenção-dos-documentos)
  - [Custo de armazenamento](#custo-de-armazenamento)
  - [O dilema central](#o-dilema-central)
- [4. Requisitos de projeto e para a solução](#4-requisitos-de-projeto-e-para-a-solução)
- [5. Solução](#5-solução)
  - [Da necessidade à solução](#da-necessidade-à-solução)
  - [Visão geral da solução](#visão-geral-da-solução)
  - [Serviços AWS utilizados](#serviços-aws-utilizados)
  - [Jornada do Cliente](#jornada-do-cliente)
  - [Arquitetura AWS](#arquitetura-aws)
  - [Resiliência e tolerância a falhas](#resiliência-e-tolerância-a-falhas)
  - [Arquitetura, AWS CAF e AWS Well-Architected Framework](#arquitetura-aws-caf-e-aws-well-architected-framework)
  - [Custos do projeto](#custos-do-projeto)
  - [Evolução e Visão de Futuro — Fase 02](#evolução-e-visão-de-futuro--fase-02)
- [6. Como o projeto foi desenvolvido](#6-como-o-projeto-foi-desenvolvido)
- [7. Infraestrutura como Código](#7-infraestrutura-como-código)
  - [Guia de como testar a aplicação](#guia-de-como-testar-a-aplicação)
- [8. Agradecimentos](#8-agradecimentos)
- [9. Referências](#9-referências)

---

# 1. Contextualização do TCC

## O que é o projeto?

Este projeto foi desenvolvido como parte de um desafio proposto pela **Escola da Nuvem**, com o objetivo de reforçar, na prática, os conhecimentos adquiridos sobre computação em nuvem e, principalmente, sobre como os serviços da AWS podem ser utilizados para resolver problemas reais de negócio.

O desafio representa uma oportunidade de sair de uma abordagem puramente conceitual e aplicar os conhecimentos estudados durante nossa preparação para a certificação **AWS Certified Cloud Practitioner** na análise e construção de uma solução arquitetural.

Mais do que simplesmente selecionar serviços da AWS, o objetivo do projeto é compreender o problema apresentado, identificar suas necessidades e restrições e, a partir disso, avaliar como diferentes recursos da nuvem podem agregar valor ao negócio.

Essa abordagem também nos levou a perceber que o projeto não trata apenas de armazenamento de arquivos. Os documentos possuem um ciclo de vida, diferentes níveis de utilização ao longo do tempo, requisitos de segurança e um valor estratégico para o negócio.

Dessa forma, decisões relacionadas à organização, acesso, retenção e custo dos dados passam a fazer parte da própria arquitetura da solução.

## Por que acreditamos que seja um tema relevante?

O tema se torna especialmente relevante quando consideramos o crescimento da utilização de Inteligência Artificial e a importância dos dados que alimentam essas soluções.

No cenário proposto, os documentos enviados pelos clientes não são apenas arquivos que precisam ser armazenados. Eles representam a base histórica utilizada para a evolução futura dos modelos de IA da empresa.

Assim, garantir que esses dados estejam organizados, protegidos, disponíveis quando necessários e economicamente sustentáveis ao longo do tempo é parte fundamental da estratégia do negócio.

Além disso, o cenário proposto está inserido em um contexto de crescimento significativo do mercado de Inteligência Artificial.

Como identificado durante a análise do cenário:

> Segundo projeção da consultoria Gartner, o investimento global em inteligência artificial deve alcançar US$ 2,59 trilhões em 2026, alta de 47% em relação ao ano anterior, com expectativa de chegar a quase US$ 3,5 trilhões em 2027.
>
> No Brasil, um estudo da IBM mostrou que 78% das empresas nacionais planejam ampliar seus investimentos em IA, e os gastos com IA no país devem ultrapassar US$ 2,4 bilhões, crescimento de 30% em relação a 2024.
>
> A adoção estratégica também disparou: 95,2% das organizações consideram a IA uma prioridade estratégica para 2026, contra apenas 32,8% que investiam na tecnologia em 2024.
>
> Cerca de 45% de todo o investimento previsto para 2026 está relacionado à infraestrutura de IA, incluindo componentes como armazenamento em nuvem, processamento e pipelines de dados.

Esses dados ajudam a contextualizar por que uma arquitetura voltada ao armazenamento e gerenciamento de dados para aplicações de IA é relevante. O crescimento dos investimentos em Inteligência Artificial também aumenta a importância da infraestrutura necessária para sustentar essas soluções.

No caso da Startup Jarva's, essa relação é particularmente importante porque os documentos recebidos pela plataforma representam justamente a matéria-prima histórica que poderá ser utilizada para o treinamento e evolução dos futuros modelos de IA.

> **Toda essa evolução da IA depende de algo fundamental: dados bem armazenados, organizados, protegidos e disponíveis para utilização. Não existe IA de qualidade sem uma base de dados histórica adequada por trás.**

Portanto, o projeto não foi escolhido apenas por envolver serviços populares de computação em nuvem ou Inteligência Artificial. Ele representa um problema cada vez mais relevante:

> **Como construir uma infraestrutura capaz de transformar o crescimento da quantidade de dados em um ativo estratégico, sem comprometer segurança, disponibilidade e sustentabilidade financeira?**

---

# 2. Contextualização do Projeto

A **Startup Jarva's** é uma empresa em fase de hipercrescimento que oferece uma plataforma SaaS voltada para **extração inteligente de dados utilizando Inteligência Artificial**.

Como parte desse serviço, a plataforma recebe documentos enviados pelos clientes, principalmente **PDFs e imagens**, que servem como insumo para o processamento da IA.

O volume previsto é de aproximadamente **50 mil novos arquivos por mês**, equivalente a cerca de **600 mil arquivos por ano**, com tendência de crescimento contínuo.

À primeira vista, o problema poderia parecer simplesmente uma questão de armazenamento. Entretanto, o cenário possui uma característica que muda completamente a forma como o problema deve ser tratado:

> **Os arquivos não podem ser deletados.**

Os documentos antigos continuam tendo valor porque representam o histórico utilizado como base para o treinamento de futuros modelos de Inteligência Artificial.

Portanto, à medida que a empresa cresce, sua quantidade de dados também cresce continuamente.

Em poucos anos, a plataforma poderá acumular milhões de documentos. Esse histórico representa não apenas uma grande quantidade de dados, mas um ativo intelectual que pode contribuir diretamente para a evolução da empresa e de seus modelos de IA.

É justamente por isso que entendemos que a Startup Jarva's não está simplesmente construindo um repositório de documentos.

> **Um repositório preserva informações. Um ativo de dados preserva informações com a intenção de gerar valor a partir delas.**

Essa mudança de perspectiva é fundamental para compreender o restante do projeto.

O armazenamento deixa de ser apenas uma infraestrutura de apoio e passa a fazer parte da própria estratégia do produto.

---

# 3. Problema a ser resolvido e impacto no negócio

O problema da Startup Jarva's é resultado da combinação de **crescimento acelerado, necessidade de isolamento entre clientes, retenção permanente dos documentos e controle dos custos de armazenamento**.

## Segurança e isolamento dos dados

A plataforma possui natureza **multi-tenant**, ou seja, diferentes clientes utilizam a mesma aplicação e sua infraestrutura.

Isso cria uma necessidade fundamental:

> **Um cliente não pode ter acesso aos documentos pertencentes a outro cliente.**

Os usuários precisam conseguir acessar seus próprios documentos de maneira rápida e segura, mas sem que uma falha de configuração, permissão ou implementação permita que arquivos de outros usuários sejam expostos.

Essa necessidade de isolamento precisa ser considerada desde o início da arquitetura, e não tratada posteriormente como uma correção.

O risco associado a esse problema não é apenas teórico. O próprio documento de fundamentação do projeto utiliza um caso real como forma de contextualizar o impacto que uma configuração inadequada pode causar:

> Em 2022, um hacker alegou ter obtido dados de cerca de um bilhão de cidadãos chineses a partir de uma implantação do Elasticsearch associada a uma agência governamental. A própria reportagem levantou dúvidas sobre a veracidade e a dimensão da alegação, portanto o caso não deve ser tratado como uma exposição comprovada nessa escala.
>
> O exemplo é utilizado como contextualização do risco associado a configurações inadequadas de infraestrutura e exposição indevida de dados.

O ponto principal, entretanto, não é afirmar que esse caso representa uma exposição comprovada naquela escala.

O valor do exemplo está em demonstrar o tipo de risco que a Startup Jarva's precisa evitar:

> **Uma configuração ou implantação inadequada pode transformar uma infraestrutura que deveria proteger dados em uma porta de acesso a eles.**

Isso é especialmente relevante para a Startup Jarva's porque a plataforma dependerá da confiança de clientes que estarão entregando seus próprios documentos ao serviço.

Uma exposição de dados, portanto, não seria apenas um incidente técnico. Ela poderia comprometer a confiança dos clientes na plataforma e, consequentemente, a própria proposta de valor da empresa.

Por esse motivo:

> **Segurança não deve ser uma camada adicionada posteriormente. Ela precisa fazer parte da arquitetura desde o primeiro arquivo recebido pela plataforma.**

---

## Retenção dos documentos

Ao contrário de sistemas em que dados antigos podem ser descartados, a Startup Jarva's possui uma exigência estratégica diferente:

> **Nenhum arquivo deve ser excluído como parte da operação normal da plataforma.**

Os documentos representam a base histórica que poderá ser utilizada para o treinamento dos próximos modelos de IA.

Dessa forma, o fato de um documento ser antigo não significa que ele perdeu seu valor. Pelo contrário, ele passa a fazer parte do patrimônio histórico de dados da empresa.

Em números, o cenário prevê aproximadamente **50 mil arquivos por mês**, o equivalente a cerca de **600 mil arquivos por ano**.

Como nenhum arquivo é descartado como parte da operação normal, esse volume continuará crescendo ao longo do tempo, podendo chegar a milhões de documentos após alguns anos de operação.

---

## Custo de armazenamento

A retenção permanente cria um segundo problema.

Se aproximadamente 50 mil arquivos são adicionados todos os meses e nenhum deles é removido, o volume armazenado continuará crescendo indefinidamente.

Manter todos esses documentos permanentemente em uma classe de armazenamento voltada para acesso frequente poderia gerar um custo incompatível com o crescimento da empresa.

Por isso, o projeto precisa considerar o **ciclo de vida dos dados**.

Documentos recentes possuem maior frequência de acesso e precisam de disponibilidade imediata, enquanto documentos históricos tendem a ser acessados com menor frequência, embora continuem tendo valor estratégico.

Na arquitetura proposta, os documentos permanecem inicialmente no **Amazon S3 Standard**, adequado ao período de maior frequência de acesso.

Após os primeiros **12 meses**, uma regra de **S3 Lifecycle** pode realizar a transição automática dos objetos para o **S3 Glacier Deep Archive**, reduzindo o custo de armazenamento dos documentos históricos que continuam precisando ser preservados.

Essa estratégia permite que o custo de armazenamento acompanhe o comportamento esperado dos dados ao longo do tempo.

---

## O dilema central

A partir desses problemas, identificamos quatro necessidades que precisam ser atendidas simultaneamente:

1. **Acesso rápido:** os clientes precisam acessar normalmente os documentos durante os primeiros 12 meses.
2. **Retenção permanente:** nenhum arquivo deve ser excluído como parte da operação normal da plataforma, pois todos fazem parte do ativo histórico da empresa.
3. **Custo sob controle:** documentos antigos devem deixar de ocupar uma classe de armazenamento de acesso frequente quando o acesso se tornar menos frequente.
4. **Isolamento e segurança:** cada documento pertence a um cliente específico e não pode ser acessado por outros clientes.

É justamente a combinação dessas necessidades que torna o problema mais interessante.

A Startup Jarva's não pode simplesmente escolher a alternativa mais barata, porque isso poderia prejudicar o acesso aos documentos.

Da mesma forma, não pode manter todo o histórico permanentemente em uma classe de armazenamento voltada para acesso frequente, porque o custo cresceria junto com a base histórica.

E também não pode priorizar apenas a facilidade de acesso sem considerar o isolamento entre clientes.

O desafio, portanto, não é simplesmente encontrar um lugar para guardar milhões de documentos.

> **O verdadeiro desafio é equilibrar segurança, acesso, retenção e custo ao longo de todo o ciclo de vida dos dados.**

Essa é a questão que a arquitetura precisa responder.

---

# 4. Requisitos de projeto e para a solução

A partir do cenário apresentado e dos problemas identificados, estabelecemos os requisitos que a solução precisa atender.

### 🔐 Segurança

A solução deve garantir o **isolamento entre os clientes**, impedindo que um usuário consiga acessar documentos pertencentes a outro.

O acesso aos documentos deve ser controlado e restrito ao proprietário autorizado.

### 📈 Escalabilidade

A solução deve suportar o crescimento contínuo da plataforma e a ingestão de aproximadamente **50 mil novos arquivos por mês**, sem depender de uma única máquina ou de uma infraestrutura que precise ser dimensionada manualmente a cada aumento de demanda.

### 🛡️ Durabilidade e retenção

Os documentos históricos não devem ser excluídos pela aplicação como parte da operação normal.

A solução deve permitir que os arquivos permaneçam preservados mesmo quando deixarem de ser acessados com frequência.

### ⚡ Disponibilidade e acesso

Os documentos enviados pelos clientes devem permanecer disponíveis para consulta durante o período em que apresentam maior frequência de acesso, especialmente durante os primeiros 12 meses.

### 💰 Economia

O custo de armazenamento deve ser reduzido conforme os documentos envelhecem.

A solução deve permitir que os arquivos continuem preservados sem exigir que todo o histórico permaneça permanentemente em uma classe de armazenamento voltada para acesso frequente.

### 📊 Operação e acompanhamento

A infraestrutura deve permitir acompanhar o funcionamento da solução, identificar falhas e manter uma trilha de auditoria das ações realizadas.

### 🔄 Reprodutibilidade

A infraestrutura deve poder ser recriada de forma consistente, permitindo que a arquitetura seja documentada e reproduzida por meio de código.

### 🛡️ Resiliência e tolerância a falhas

A solução deve evitar dependências em servidores ou componentes individuais cuja indisponibilidade possa interromper completamente o funcionamento da plataforma.

Sempre que possível, a arquitetura deve utilizar serviços gerenciados capazes de oferecer alta disponibilidade como parte de sua operação, reduzindo a necessidade de gerenciamento manual de infraestrutura.

Além disso, a solução deve ser capaz de continuar preservando os documentos e mantendo os principais serviços disponíveis mesmo diante de falhas pontuais de componentes ou da infraestrutura subjacente.

---

# 5. Solução

## Da necessidade à solução

A partir desses requisitos, fica claro que o desafio da Startup Jarva's não está apenas em armazenar uma grande quantidade de documentos.

A arquitetura precisa acompanhar o crescimento da empresa, proteger os dados de cada cliente, preservar o histórico como um ativo estratégico e, ao mesmo tempo, manter os custos sob controle.

É a partir dessas necessidades que chegamos à proposta de arquitetura deste projeto.

A escolha dos serviços AWS não parte, portanto, da tecnologia em si, mas dos problemas que precisam ser resolvidos e dos requisitos que a solução precisa atender.

A proposta desenvolvida utiliza uma arquitetura **serverless**, baseada em serviços gerenciados da AWS, reduzindo a necessidade de gerenciamento de infraestrutura e permitindo que a solução acompanhe a demanda da plataforma.

A arquitetura também separa responsabilidades importantes do sistema:

- Autenticação;
- Controle de acesso;
- Lógica de negócio;
- Armazenamento dos documentos;
- Gerenciamento de metadados;
- Observabilidade;
- Auditoria;
- Gerenciamento do ciclo de vida dos dados;
- Provisionamento da infraestrutura.

---

## Visão geral da solução

A solução foi projetada para que o cliente possa enviar e acessar documentos sem receber acesso direto e irrestrito ao ambiente de armazenamento.

O fluxo começa com a autenticação do usuário por meio do **Amazon Cognito**.

Após a autenticação, o usuário recebe os tokens necessários para acessar a aplicação e realizar solicitações à API.

As requisições são direcionadas ao **Amazon API Gateway**, que atua como ponto de entrada da API e integra-se à lógica da aplicação.

As solicitações são encaminhadas para funções do **AWS Lambda**, responsáveis por aplicar as regras de negócio e validar se o usuário possui autorização para realizar determinada operação.

Os metadados dos documentos e as informações de propriedade são armazenados no **Amazon DynamoDB**.

Dessa forma, antes de permitir operações como consulta, download ou geração de uma URL de acesso, a aplicação pode verificar a relação entre o usuário autenticado e o documento solicitado.

Os arquivos são armazenados em um bucket privado do **Amazon S3**, organizado de acordo com a estrutura definida pela aplicação.

O acesso aos objetos ocorre por meio de **URLs pré-assinadas e temporárias**, geradas somente após a validação das permissões necessárias.

Essa abordagem contribui para o isolamento entre clientes e evita a exposição pública do bucket.

O usuário recebe autorização apenas para realizar a operação específica solicitada e dentro de um período limitado.

### Estratégia de armazenamento

Durante os primeiros **12 meses**, os documentos permanecem no **Amazon S3 Standard**, atendendo ao requisito de acesso frequente e disponibilidade imediata.

Após esse período, uma regra de **S3 Lifecycle** pode realizar a transição automática dos objetos para o **S3 Glacier Deep Archive**.

Essa classe é adequada ao armazenamento de longo prazo de dados que precisam ser preservados, mas que apresentam baixa frequência de acesso.

A transição permite reduzir o custo de armazenamento sem eliminar os documentos históricos.

### Preservação dos documentos

O **S3 Object Lock** contribui para proteger os objetos contra exclusão ou alteração durante o período de retenção configurado.

A configuração da retenção deve ser definida de acordo com os requisitos de negócio da Startup Jarva's.

Dessa forma, o Object Lock funciona como uma camada adicional de proteção dos documentos, enquanto o S3 Lifecycle é responsável pela estratégia de transição entre classes de armazenamento.

### Criptografia

Os objetos armazenados no Amazon S3 são protegidos por **criptografia server-side**, utilizando a criptografia padrão oferecida pelo serviço.

Em uma evolução futura, o **AWS KMS** poderá ser incorporado para proporcionar maior controle sobre as chaves criptográficas e suas respectivas políticas de acesso.

O resultado é uma arquitetura que busca equilibrar **segurança, escalabilidade, resiliência, preservação histórica, experiência do usuário e sustentabilidade dos custos**.

Ao utilizar serviços gerenciados e serverless, a solução também reduz a dependência de componentes individuais administrados pela equipe.

Dessa forma, a arquitetura pode se beneficiar dos mecanismos de disponibilidade e tolerância a falhas oferecidos pelos serviços AWS utilizados, mantendo o foco da equipe na evolução da aplicação e nas necessidades do negócio.

---

## Serviços AWS utilizados

| Serviço | Papel na solução |
|---|---|
| **Amazon Cognito** | Autenticação e gerenciamento da identidade dos usuários |
| **Amazon API Gateway** | Camada de entrada da API, controle das solicitações e integração com a lógica da aplicação |
| **AWS Lambda** | Execução da lógica de negócio, validações e geração de URLs pré-assinadas |
| **Amazon DynamoDB** | Armazenamento dos metadados e informações de propriedade dos documentos |
| **Amazon S3** | Armazenamento seguro, durável e escalável dos documentos |
| **S3 Lifecycle** | Gerenciamento do ciclo de vida e transição dos documentos históricos |
| **S3 Glacier Deep Archive** | Armazenamento histórico de longo prazo para documentos com baixa frequência de acesso |
| **S3 Object Lock** | Proteção dos objetos contra exclusão ou alteração durante o período de retenção configurado |
| **S3 Transfer Acceleration** | Otimização da transferência de arquivos entre clientes geograficamente distribuídos e o Amazon S3 |
| **AWS IAM** | Controle de permissões seguindo o princípio do menor privilégio |
| **Amazon CloudWatch** | Monitoramento, métricas, logs e acompanhamento operacional |
| **AWS CloudTrail** | Registro e auditoria das ações realizadas na conta e nos serviços AWS |
| **AWS CloudFormation** | Provisionamento e reprodução da infraestrutura por meio de código |

---

## Jornada do Cliente

A arquitetura técnica mostra como os serviços se conectam.

Entretanto, para compreender a solução sob a perspectiva de quem utiliza a plataforma, também desenvolvemos uma visão focada na **Jornada do Cliente**.

Essa jornada representa o caminho percorrido pelo usuário desde o acesso à plataforma até a preservação histórica de seus documentos.

<p align="center">
  <img width="1536" height="1024" alt="Jornada do Cliente - Plataforma SaaS de Gestão de Documentos com IA" src="https://github.com/user-attachments/assets/205a90b4-dfd8-44de-83bf-c4a7f09828fc" />
</p>

A jornada foi organizada em três momentos principais:

### 1. Acesso e envio

O cliente acessa a plataforma, realiza sua autenticação e envia um documento para o processamento da aplicação.

Nesse momento, o objetivo é proporcionar uma experiência simples ao usuário sem abrir mão da segurança e da identificação correta da propriedade do documento.

### 2. Proteção e utilização

Após o envio, o documento é associado à conta do cliente e armazenado de forma segura.

Quando o usuário deseja consultar ou baixar um arquivo, a plataforma verifica sua identidade e suas permissões antes de liberar o acesso.

Dessa forma, o cliente não recebe acesso irrestrito ao ambiente de armazenamento.

O acesso é concedido somente ao documento solicitado e de forma controlada.

### 3. Preservação histórica

Com o passar do tempo, os documentos continuam preservados como parte do histórico da empresa.

Durante os primeiros 12 meses, os arquivos permanecem em uma classe adequada ao acesso frequente.

Após esse período, a estratégia de ciclo de vida permite realizar a transição para uma classe de armazenamento histórico de menor custo, mantendo os documentos preservados para futuras necessidades do negócio.

Essa visão reforça um dos princípios centrais do projeto:

> **A segurança e a preservação dos dados devem estar presentes durante toda a jornada do cliente, e não apenas no momento do armazenamento.**

---

## Arquitetura AWS

A visão técnica da solução apresenta os serviços AWS utilizados e o fluxo principal de comunicação entre os componentes da arquitetura.

<p align="center">
  <img width="1536" height="1024" alt="Arquitetura AWS - Plataforma SaaS de Gestão de Documentos com IA" src="https://github.com/user-attachments/assets/e90aaf15-e642-45ec-99ba-cd88689b85d8" />
</p>

O fluxo principal pode ser resumido da seguinte forma:

1. O usuário realiza o login na plataforma utilizando o **Amazon Cognito**.
2. Após a autenticação, o usuário recebe os tokens necessários para acessar a aplicação.
3. As solicitações são enviadas para o **Amazon API Gateway**, que atua como ponto de entrada da API.
4. O **AWS Lambda** processa a solicitação e aplica as regras de negócio.
5. Quando necessário, a função consulta os metadados no **Amazon DynamoDB** para validar a propriedade e a autorização relacionadas ao documento.
6. Após a validação, a aplicação gera uma URL pré-assinada para a operação solicitada no **Amazon S3**.
7. O usuário realiza o upload ou download diretamente no S3 utilizando essa autorização temporária.
8. Os documentos permanecem armazenados em um bucket privado.
9. Durante os primeiros 12 meses, os documentos permanecem no **S3 Standard**.
10. Após esse período, uma regra de **S3 Lifecycle** pode realizar a transição dos documentos para o **S3 Glacier Deep Archive**.
11. O **S3 Object Lock** protege os objetos de acordo com o período de retenção configurado.

Além do fluxo principal, a arquitetura incorpora mecanismos de observabilidade, auditoria, controle de acesso, otimização de custos e infraestrutura como código.

É importante destacar que serviços como **S3 Lifecycle**, **S3 Glacier Deep Archive** e **S3 Object Lock** não representam etapas pelas quais uma requisição do usuário necessariamente passa em tempo real.

Eles fazem parte da estratégia de gerenciamento e preservação dos dados ao longo de seu ciclo de vida.

O **S3 Transfer Acceleration**, por sua vez, atua na transferência dos arquivos entre clientes geograficamente distribuídos e o Amazon S3, quando esse recurso estiver habilitado para o cenário.

---

## Resiliência e tolerância a falhas

Além de segurança e escalabilidade, a arquitetura também foi pensada para reduzir a dependência de componentes individuais que poderiam representar pontos únicos de falha.

Uma das principais decisões da Fase 01 foi utilizar uma arquitetura baseada em serviços **serverless e gerenciados pela AWS**.

Isso significa que a equipe não precisa depender de um único servidor, máquina virtual ou instância para manter o funcionamento da aplicação.

Os principais componentes da solução, como **Amazon Cognito**, **Amazon API Gateway**, **AWS Lambda**, **Amazon DynamoDB** e **Amazon S3**, são serviços gerenciados que operam sobre uma infraestrutura fornecida pela AWS.

Dessa forma, a aplicação não depende de uma única Zona de Disponibilidade configurada manualmente pela equipe para executar seu fluxo principal.

A responsabilidade pela infraestrutura subjacente e pela disponibilidade dos serviços é compartilhada com a AWS de acordo com as características e os acordos de nível de serviço de cada serviço.

### O que acontece se um componente falhar?

A arquitetura foi projetada para reduzir o impacto de falhas relacionadas à infraestrutura de componentes individuais.

Por exemplo, não existe uma única instância EC2 responsável por processar todas as solicitações da plataforma.

A lógica da aplicação é executada pelo **AWS Lambda**, enquanto os documentos e metadados são armazenados em serviços gerenciados como **Amazon S3** e **Amazon DynamoDB**.

Essa abordagem reduz o risco de que a falha de um único servidor administrado pela aplicação interrompa completamente o sistema.

Entretanto, é importante destacar que:

> **Resiliência não significa que a aplicação é imune a qualquer tipo de falha.**

Falhas relacionadas à lógica da aplicação, configurações incorretas, permissões inadequadas ou indisponibilidades de serviços externos ainda precisam ser consideradas durante a evolução do sistema.

Por esse motivo, a arquitetura incorpora mecanismos de **observabilidade**, utilizando o **Amazon CloudWatch**, e de **auditoria**, utilizando o **AWS CloudTrail**, permitindo identificar problemas e acompanhar o comportamento operacional da solução.

### Resiliência como parte da evolução da arquitetura

A Fase 01 estabelece uma base resiliente por meio da utilização de serviços gerenciados e da redução de pontos únicos de falha sob responsabilidade direta da equipe.

Conforme a plataforma cresça e seus requisitos de disponibilidade se tornem mais exigentes, novos mecanismos poderão ser avaliados, como estratégias avançadas de recuperação, replicação de dados e planos de continuidade de negócio.

Dessa forma, a resiliência é tratada como um princípio presente desde a concepção da solução, mas também como uma área que pode evoluir de acordo com a criticidade e a escala do negócio.

---

## Arquitetura, AWS CAF e AWS Well-Architected Framework

A construção da solução também foi orientada por boas práticas de arquitetura em nuvem, considerando princípios presentes no **AWS Cloud Adoption Framework (AWS CAF)** e no **AWS Well-Architected Framework**.

O AWS CAF contribui para analisar a adoção da nuvem de forma mais ampla, considerando aspectos que vão além da tecnologia.

No contexto deste projeto, ele ajuda a relacionar a arquitetura às necessidades do negócio, à segurança, à operação e à gestão dos recursos utilizados.

Já o AWS Well-Architected Framework oferece princípios técnicos para avaliar se uma arquitetura está sendo construída de maneira segura, confiável, eficiente e sustentável.

A relação da arquitetura com esses princípios pode ser observada da seguinte forma:

### 🔐 Segurança

O projeto prioriza a autenticação dos usuários, o controle de permissões e a validação da propriedade dos documentos antes da liberação do acesso.

O **Amazon Cognito**, o **AWS IAM**, o **Amazon API Gateway**, o **AWS Lambda** e o uso de URLs pré-assinadas contribuem para que o acesso aos dados seja controlado e limitado às operações autorizadas.

Os objetos armazenados no Amazon S3 também são protegidos por criptografia server-side.

Na Fase 02, o **AWS KMS** poderá ser incorporado para ampliar o controle sobre as chaves criptográficas.

### 📈 Escalabilidade e performance

A utilização de serviços serverless permite que a solução acompanhe a demanda sem depender de uma única máquina responsável pelo processamento das solicitações.

O **Amazon API Gateway**, o **AWS Lambda**, o **Amazon DynamoDB** e o **Amazon S3** oferecem uma base gerenciada para o crescimento da aplicação.

O **S3 Transfer Acceleration** complementa essa estratégia ao otimizar a transferência de arquivos em cenários nos quais os clientes estão geograficamente distribuídos.

### 🛡️ Confiabilidade e resiliência

A arquitetura foi projetada para reduzir a dependência de componentes individuais administrados pela equipe.

A utilização de serviços gerenciados como **Amazon Cognito**, **Amazon API Gateway**, **AWS Lambda**, **Amazon DynamoDB** e **Amazon S3** permite que a aplicação se apoie em uma infraestrutura fornecida e operada pela AWS, sem depender de um único servidor responsável pelo funcionamento da plataforma.

Essa escolha contribui para a resiliência da solução, reduzindo pontos únicos de falha associados à infraestrutura tradicional e permitindo que a aplicação acompanhe o crescimento do negócio sem exigir o gerenciamento direto de servidores.

Além disso, o **Amazon CloudWatch** permite acompanhar o comportamento operacional da aplicação e identificar possíveis falhas, enquanto a infraestrutura como código facilita a reprodução consistente do ambiente quando necessário.

### 🗂️ Durabilidade e preservação histórica

O **Amazon S3** oferece uma base durável para o armazenamento dos documentos, enquanto a estratégia de ciclo de vida permite preservar o histórico ao longo do tempo.

Durante os primeiros 12 meses, os documentos permanecem no **S3 Standard**.

Após esse período, o **S3 Lifecycle** pode realizar a transição para o **S3 Glacier Deep Archive**, permitindo reduzir os custos de armazenamento dos documentos históricos sem eliminá-los.

O **S3 Object Lock** reforça a proteção dos objetos contra exclusão ou alteração durante o período de retenção configurado.

Essa combinação permite tratar os documentos não apenas como arquivos armazenados, mas como um ativo histórico que continua disponível para gerar valor para o negócio ao longo do tempo.

### 💰 Otimização de custos

A arquitetura reconhece que documentos recentes e históricos possuem padrões de acesso diferentes.

Por esse motivo, a estratégia de **S3 Lifecycle** e **S3 Glacier Deep Archive** permite adequar a classe de armazenamento ao comportamento esperado dos dados.

Os documentos permanecem inicialmente em uma classe adequada ao acesso frequente e, após 12 meses, podem ser transferidos para uma classe voltada ao armazenamento histórico de longo prazo.

Além disso, serviços serverless reduzem a necessidade de manter servidores provisionados e ociosos exclusivamente para suportar a aplicação.

### 📊 Excelência operacional

O **Amazon CloudWatch** permite acompanhar logs, métricas e possíveis alarmes relacionados à operação da solução.

O **AWS CloudTrail** complementa essa visão mantendo registros das ações realizadas, contribuindo para auditoria e governança.

Por fim, o **AWS CloudFormation** permite que a infraestrutura seja provisionada e reproduzida por meio de código, reduzindo inconsistências entre ambientes e facilitando a evolução da arquitetura.

---

## Custos do projeto

> 🚧 **Em desenvolvimento**
>
> Nesta seção serão apresentados os custos estimados da solução, as principais variáveis que influenciam o consumo dos serviços AWS e a estratégia adotada para acompanhar e otimizar os gastos da infraestrutura.

---

## Evolução e Visão de Futuro — Fase 02

A arquitetura apresentada na Fase 01 foi desenvolvida para atender aos principais requisitos do cenário proposto, priorizando segurança, isolamento entre clientes, escalabilidade, resiliência, retenção dos documentos, otimização de custos, observabilidade e reprodutibilidade da infraestrutura.

Como parte da evolução da solução, identificamos alguns pontos que podem ser aprimorados em uma segunda fase do projeto.

Essas melhorias não são necessárias para que a arquitetura inicial atenda aos requisitos definidos, mas representam oportunidades para elevar o nível de segurança, governança, resiliência e maturidade operacional da plataforma conforme o negócio cresça.

A Fase 02 não representa uma substituição da arquitetura atual.

Ela parte da base construída na Fase 01 e avalia quais novos recursos e estratégias passam a fazer sentido à medida que aumentam o número de usuários, o volume de documentos, a criticidade da operação e a sensibilidade dos dados armazenados.

### 🔐 Fase 02 — Evolução da Segurança e Governança

A Fase 02 tem como principal objetivo fortalecer a proteção dos dados e o gerenciamento de informações sensíveis, complementando os mecanismos de segurança já presentes na Fase 01.

Os serviços avaliados para esta etapa são:

| Serviço | Objetivo na Fase 02 |
|---|---|
| **AWS KMS** | Gerenciamento centralizado de chaves criptográficas e maior controle sobre a proteção dos dados |
| **AWS Secrets Manager** | Armazenamento e gerenciamento seguro de credenciais, segredos e informações sensíveis utilizadas pela aplicação |
| **Amazon Macie** | Descoberta e identificação de dados sensíveis armazenados no Amazon S3, apoiando a classificação e a proteção das informações |

A adoção desses serviços deve ser avaliada considerando o crescimento da plataforma, o nível de sensibilidade dos documentos armazenados e o impacto financeiro de sua utilização.

A proposta não é adicionar serviços simplesmente para aumentar a quantidade de componentes da arquitetura.

Cada recurso deve ser incorporado quando houver uma necessidade concreta que justifique seu uso, considerando segurança, governança, complexidade operacional e custo.

### 🚀 Como a solução pode evoluir?

A evolução da plataforma pode ser analisada a partir de algumas perguntas importantes:

- Como a solução poderia atender a um volume significativamente maior de usuários e documentos?
- Como aumentar o nível de proteção dos dados conforme a quantidade e a sensibilidade das informações cresçam?
- Como identificar e monitorar automaticamente a presença de informações sensíveis nos documentos armazenados?
- Como melhorar o gerenciamento de credenciais e informações confidenciais utilizadas pela aplicação?
- Como aumentar o controle sobre as chaves utilizadas para proteger os dados?
- Como reduzir ainda mais o impacto de falhas e indisponibilidades em componentes críticos da solução?
- Como estabelecer estratégias de recuperação e continuidade caso os requisitos de disponibilidade da plataforma se tornem mais rigorosos?
- Como manter o crescimento da plataforma sustentável sem aumentar os custos de forma desproporcional?

A Fase 02 representa, portanto, uma evolução natural da arquitetura, na qual mecanismos adicionais de segurança e governança podem ser incorporados conforme as necessidades do negócio se tornem mais complexas.

### 📈 Visão de futuro

Em um cenário de crescimento da Startup Jarva's, a arquitetura poderá evoluir para atender a um volume maior de usuários, documentos e processamento, mantendo os princípios que orientaram a solução desde sua concepção.

Entre as possibilidades de evolução estão:

- **Maior proteção criptográfica:** utilização do AWS KMS para ampliar o controle sobre as chaves criptográficas e os mecanismos de proteção dos dados.
- **Gestão de informações sensíveis:** utilização do AWS Secrets Manager para centralizar e proteger credenciais e outros segredos utilizados pela aplicação.
- **Descoberta de dados sensíveis:** utilização do Amazon Macie para identificar e classificar informações potencialmente sensíveis armazenadas no Amazon S3.
- **Maior resiliência:** avaliação de mecanismos adicionais de recuperação e continuidade de negócio conforme os requisitos de disponibilidade e criticidade da plataforma aumentem.
- **Maior governança:** ampliação dos mecanismos de auditoria, monitoramento e controle conforme a plataforma cresça.
- **Escalabilidade:** evolução da arquitetura para suportar um aumento significativo no número de usuários e documentos sem depender de componentes individuais que limitem o crescimento.
- **Otimização de custos:** revisão contínua das estratégias de armazenamento e utilização dos serviços conforme o comportamento real da aplicação.

Essas melhorias não precisam necessariamente ser implementadas na primeira versão da solução.

O objetivo desta etapa é demonstrar que a arquitetura foi pensada não apenas para atender ao cenário atual, mas também para permitir uma evolução consistente conforme o negócio cresça.

> **A Fase 01 resolve o problema atual. A Fase 02 prepara a arquitetura para os desafios que surgem com o crescimento e a maturidade da plataforma.**

---

# 6. Como o projeto foi desenvolvido

<p align="center">
  <img width="1905" height="1065" alt="Image" src="https://github.com/user-attachments/assets/9b9cb4cf-11d1-4d90-8950-c318547d43de" />
</p>

O desenvolvimento do projeto foi conduzido a partir de uma abordagem de **gestão ágil**, combinando **Scrum**, **Kanban** e **PDCA** para organizar as atividades, acompanhar a evolução da solução e promover ciclos contínuos de análise, desenvolvimento e revisão.

Como o projeto envolvia não apenas a construção de uma arquitetura técnica, mas também a análise do problema de negócio, o levantamento de requisitos, a avaliação de serviços AWS e a elaboração da documentação, cada uma dessas práticas contribuiu para uma dimensão diferente do processo.

## Sprints semanais (Scrum)

O trabalho foi organizado em **Sprints semanais**, nas quais eram definidos os principais objetivos do ciclo. Reuniões periódicas acompanhavam o andamento das tarefas, discutiam dificuldades, alinhavam decisões e revisavam entregas.

Essa organização permitiu dividir um problema inicialmente amplo em entregas menores e progressivas: em vez de definir toda a arquitetura de uma só vez, as decisões foram amadurecidas conforme a equipe aprofundava sua compreensão do problema, dos requisitos e das possibilidades oferecidas pelos serviços AWS.

## Quadro Kanban

O fluxo de trabalho foi visualizado em um **quadro Kanban no Trello**, com as atividades organizadas em etapas — **To Do, In Progress, In Review e Done**. O quadro também centralizava anotações de contextualização, planejamento e sugestões, dando à equipe uma visão compartilhada do que precisava ser feito, do que estava em andamento e do que já havia sido concluído.

## PDCA e melhoria contínua

De forma complementar às Sprints, aplicamos o ciclo **PDCA (Plan, Do, Check, Act)** para avaliar e aprimorar continuamente as decisões:

1. **Plan:** identificar prioridades e definir os objetivos do ciclo.
2. **Do:** executar as atividades planejadas.
3. **Check:** revisar resultados e decisões, identificando pontos de melhoria.
4. **Act:** incorporar os aprendizados, ajustando o planejamento seguinte.

Esse ciclo foi essencial porque várias decisões arquiteturais amadureceram ao longo do projeto: à medida que a análise dos requisitos avançava, novas necessidades e oportunidades de melhoria eram identificadas e incorporadas.

## Como as abordagens se conectam

**Scrum** deu estrutura aos ciclos de trabalho, **Kanban** trouxe visibilidade ao fluxo das atividades, e **PDCA** garantiu a avaliação e melhoria contínua do processo:

**Planejamento → Sprint → Execução → Revisão → Ajustes → Próxima Sprint**

Essa combinação equilibrou organização e flexibilidade — havia objetivos claros para cada ciclo, mas também espaço para revisar decisões conforme novos aspectos do problema surgiam.

## Gestão das decisões e evolução da arquitetura

As decisões não foram tratadas como tarefas técnicas isoladas: cada escolha foi relacionada aos requisitos do projeto, às necessidades do negócio e a aspectos como **segurança, escalabilidade, resiliência, disponibilidade, retenção e custos**. A evolução seguiu um fluxo progressivo:

**Entendimento do problema → Levantamento de requisitos → Análise de alternativas → Definição da solução → Revisão → Evolução da arquitetura**

Esse processo também permitiu distinguir o que era necessário para atender aos requisitos da **Fase 01** daquilo que poderia ser incorporado depois, como parte da evolução da plataforma. Recursos como **AWS KMS, AWS Secrets Manager e Amazon Macie**, por exemplo, foram reservados para uma possível **Fase 02**, evitando adicionar complexidade à arquitetura inicial sem uma necessidade concreta que a justificasse.

## Resultado da abordagem de gestão

A combinação de **Scrum, Kanban e PDCA** permitiu que a equipe acompanhasse a evolução da solução, revisasse decisões e incorporasse melhorias de forma incremental e colaborativa — resultando em um processo no qual **gestão e arquitetura evoluíram juntas**.

> **O projeto não foi desenvolvido como uma sequência linear de decisões. Ele evoluiu em ciclos de planejamento, execução, revisão e melhoria contínua, permitindo que a solução amadurecesse junto com o entendimento do problema.**

---

# 7. Infraestrutura como Código

A infraestrutura da solução foi planejada para ser reproduzível e consistente entre diferentes ambientes.

A utilização de **Infrastructure as Code (IaC)** permite transformar a arquitetura definida no projeto em recursos provisionados por meio de código.

> 🚧 **Em desenvolvimento**
>
> O código da infraestrutura e sua documentação serão disponibilizados nesta seção.

### 🔗 Acesse o código da infraestrutura

> **[Inserir aqui o hyperlink para o repositório ou diretório contendo o código de Infrastructure as Code]**

---

## Guia de como testar a aplicação

> 🚧 **Em desenvolvimento**
>
> Nesta seção será disponibilizado um guia com as instruções necessárias para testar e validar o funcionamento da aplicação.

---

# 8. Agradecimentos

Este projeto foi construído de forma colaborativa como parte de uma jornada de aprendizado e aplicação prática dos conhecimentos adquiridos durante a preparação em computação em nuvem.

Agradecemos à **Escola da Nuvem**, aos professores, mentores e a todos os integrantes da equipe que contribuíram com análises, ideias e diferentes perspectivas ao longo do desenvolvimento do projeto.

<!-- ESPAÇO RESERVADO PARA FOTO DO GRUPO -->

<p align="center">
  <em>Foto da equipe em breve.</em>
</p>

---

# 9. Referências

### 1. Amazon S3 — Block Public Access

Configurações de bloqueio de acesso público e como essas configurações podem impedir políticas ou permissões que permitiriam acesso público aos objetos.

### 2. Amazon S3 — URLs pré-assinadas

Documentação oficial sobre URLs pré-assinadas e como conceder acesso temporário e controlado a objetos armazenados no Amazon S3.

### 3. AWS re:Post — Acesso por prefixo

Exemplo oficial de política de IAM que utiliza a condição `s3:prefix` e variáveis de identidade para restringir usuários aos seus próprios prefixos dentro de um bucket compartilhado.

### 4. Amazon S3 — Gerenciamento do ciclo de vida de objetos

Documentação oficial sobre regras de S3 Lifecycle e transição de objetos entre diferentes classes de armazenamento, incluindo cenários de armazenamento histórico e de longo prazo.

### 5. Amazon API Gateway — Features

Documentação sobre o papel do API Gateway como camada de publicação de APIs, integração com AWS Lambda, controle de tráfego e recursos de segurança e monitoramento.

### 6. AWS Lambda

Documentação oficial sobre o modelo de execução serverless, execução orientada a eventos, integração com outros serviços AWS e cobrança baseada no uso.

### 7. G1 Tecnologia — Reportagem jornalística

Caso da Polícia de Xangai (2022): alegação de exposição de registros associados a cerca de 1 bilhão de cidadãos por uma possível falha de configuração em uma infraestrutura de dados.

O caso é utilizado exclusivamente como contextualização do risco relacionado à exposição indevida de dados e não como comprovação técnica de uma exposição nessa escala.

### 8. IBM — Cost of a Data Breach Report 2026

Relatório anual da IBM sobre custos, causas e impactos relacionados a violações de dados, utilizado como referência para contextualizar os riscos associados à segurança de informações e à evolução da Inteligência Artificial.

### 9. Gartner — Worldwide AI Spending

Projeções da Gartner sobre o crescimento dos investimentos globais em Inteligência Artificial e a importância crescente da infraestrutura necessária para suportar essas soluções.

---

<p align="center">
  <strong>☁️ Startup Jarva's</strong><br>
  Plataforma SaaS de Gestão de Documentos com IA
</p>
