<div align="center">

# ☁️ Startup Jarva's
### Plataforma SaaS de Gestão de Documentos com IA

<img width="1672" height="940" alt="Capa do projeto - Startup Jarva's" src="https://github.com/user-attachments/assets/dc2e1360-263c-47af-b3fc-912f140d9fa7" />

<br/>

[![🇧🇷 Português](https://img.shields.io/badge/🇧🇷-Português-009c3b?style=for-the-badge)](./README.md)
[![🇺🇸 English](https://img.shields.io/badge/🇺🇸-English-lightgrey?style=for-the-badge)](./README.en.md)

<br/>

[![AWS](https://img.shields.io/badge/AWS-Cloud%20Architecture-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)](#5-solução)
[![Serverless](https://img.shields.io/badge/Arquitetura-Serverless-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white)](#5-solução)
[![IaC](https://img.shields.io/badge/IaC-CloudFormation-527FFF?style=for-the-badge&logo=amazonaws&logoColor=white)](#7-infraestrutura-como-código)
[![Status](https://img.shields.io/badge/Fase%2001-Concluída-brightgreen?style=for-the-badge)](#5-solução)
[![Fase 02](https://img.shields.io/badge/Fase%2002-Planejada-lightgrey?style=for-the-badge)](#-evolução-e-visão-de-futuro--fase-02)

[![Amazon S3](https://img.shields.io/badge/Amazon%20S3-569A31?style=flat-square&logo=amazons3&logoColor=white)](#-serviços-aws-utilizados)
[![AWS Lambda](https://img.shields.io/badge/AWS%20Lambda-FF9900?style=flat-square&logo=awslambda&logoColor=white)](#-serviços-aws-utilizados)
[![Amazon DynamoDB](https://img.shields.io/badge/Amazon%20DynamoDB-4053D6?style=flat-square&logo=amazondynamodb&logoColor=white)](#-serviços-aws-utilizados)
[![Amazon Cognito](https://img.shields.io/badge/Amazon%20Cognito-DD344C?style=flat-square&logo=amazoncognito&logoColor=white)](#-serviços-aws-utilizados)
[![API Gateway](https://img.shields.io/badge/Amazon%20API%20Gateway-FF4F8B?style=flat-square&logo=amazonapigateway&logoColor=white)](#-serviços-aws-utilizados)
[![CloudFormation](https://img.shields.io/badge/AWS%20CloudFormation-527FFF?style=flat-square&logo=amazonaws&logoColor=white)](#7-infraestrutura-como-código)

*Projeto desenvolvido como parte do desafio proposto pela **Escola da Nuvem** para aplicação prática dos conhecimentos em AWS Cloud e arquitetura de soluções em nuvem.*

</div>

---

<details open>
<summary><h2>📌 Sumário</h2></summary>

- [1️⃣ Contextualização do TCC](#1-contextualização-do-tcc)
  - [1.1 💡 O que é o projeto?](#-o-que-é-o-projeto)
  - [1.2 📊 Por que acreditamos que seja um tema relevante?](#-por-que-acreditamos-que-seja-um-tema-relevante)

- [2️⃣ Contextualização do Projeto](#2-contextualização-do-projeto)

- [3️⃣ Problema a ser resolvido e impacto no negócio](#3-problema-a-ser-resolvido-e-impacto-no-negócio)
  - [3.1 🔒 Segurança e isolamento dos dados](#-segurança-e-isolamento-dos-dados)
  - [3.2 🗃️ Retenção dos documentos](#️-retenção-dos-documentos)
  - [3.3 💵 Custo de armazenamento](#-custo-de-armazenamento)
  - [3.4 ⚖️ O dilema central](#️-o-dilema-central)

- [4️⃣ Requisitos de projeto e para a solução](#4-requisitos-de-projeto-e-para-a-solução)

- [5️⃣ Solução](#5-solução)
  - [5.1 🧩 Da necessidade à solução](#-da-necessidade-à-solução)
  - [5.2 🔭 Visão geral da solução](#-visão-geral-da-solução)
  - [5.3 🛠️ Serviços AWS utilizados](#️-serviços-aws-utilizados)
  - [5.4 🚶 Jornada do Cliente](#-jornada-do-cliente)
  - [5.5 🏗️ Arquitetura AWS](#️-arquitetura-aws)
  - [5.6 🛡️ Resiliência e tolerância a falhas](#resiliência-e-tolerância-a-falhas)
  - [5.7 🧭 Arquitetura, AWS CAF e AWS Well-Architected Framework](#-arquitetura-aws-caf-e-aws-well-architected-framework)
  - [5.8 💰 Custos do projeto](#-custos-do-projeto)
  - [5.9 🚀 Evolução e Visão de Futuro — Fase 02](#-evolução-e-visão-de-futuro--fase-02)

- [6️⃣ Como o projeto foi desenvolvido](#6-como-o-projeto-foi-desenvolvido)

- [7️⃣ Infraestrutura como Código](#7-infraestrutura-como-código)

- [8️⃣ Vídeo de Apresentação](#8--vídeo-de-apresentação)

- [9️⃣ Agradecimentos](#9-agradecimentos)

- [🔟 Referências](#10-referências)

</details>

---

# 1. Contextualização do TCC

## 💡 O que é o projeto?

Este projeto foi desenvolvido como parte de um desafio proposto pela **Escola da Nuvem**, com o objetivo de reforçar, na prática, os conhecimentos adquiridos sobre computação em nuvem e, principalmente, sobre como os serviços da AWS podem ser utilizados para resolver problemas reais de negócio.

O desafio representa uma oportunidade de sair de uma abordagem puramente conceitual e aplicar os conhecimentos estudados durante nossa preparação para a certificação **AWS Certified Cloud Practitioner** na análise e construção de uma solução arquitetural.

Mais do que simplesmente selecionar serviços da AWS, o objetivo do projeto é compreender o problema apresentado, identificar suas necessidades e restrições e, a partir disso, avaliar como diferentes recursos da nuvem podem agregar valor ao negócio.

Essa abordagem também nos levou a perceber que o projeto envolve muito mais do que armazenamento de arquivos. Os documentos possuem um ciclo de vida, diferentes níveis de utilização ao longo do tempo, requisitos de segurança e um valor estratégico para o negócio.

Dessa forma, decisões relacionadas à organização, acesso, retenção e custo dos dados passam a fazer parte da própria arquitetura da solução.

## 📊 Por que acreditamos que seja um tema relevante?

O tema se torna especialmente relevante quando consideramos o crescimento da utilização de Inteligência Artificial e a importância dos dados que alimentam essas soluções.

No cenário proposto, os documentos enviados pelos clientes representam a base histórica utilizada para a evolução futura dos modelos de IA da empresa.

Assim, garantir que esses dados estejam organizados, protegidos, disponíveis quando necessários e economicamente sustentáveis ao longo do tempo é parte fundamental da estratégia do negócio.

Além disso, o cenário proposto está inserido em um contexto de crescimento significativo do mercado de Inteligência Artificial.

Como identificado durante a análise do cenário:

> 📈 Segundo projeção da consultoria Gartner, o investimento global em inteligência artificial deve alcançar US$ 2,59 trilhões em 2026, alta de 47% em relação ao ano anterior, com expectativa de chegar a quase US$ 3,5 trilhões em 2027.
>
> 🇧🇷 No Brasil, um estudo da IBM mostrou que 78% das empresas nacionais planejam ampliar seus investimentos em IA, e os gastos com IA no país devem ultrapassar US$ 2,4 bilhões, crescimento de 30% em relação a 2024.
>
> 🎯 A adoção estratégica também disparou: 95,2% das organizações consideram a IA uma prioridade estratégica para 2026, contra apenas 32,8% que investiam na tecnologia em 2024.
>
> 🏗️ Cerca de 45% de todo o investimento previsto para 2026 está relacionado à infraestrutura de IA, incluindo componentes como armazenamento em nuvem, processamento e pipelines de dados.

Esses dados ajudam a contextualizar por que uma arquitetura voltada ao armazenamento e gerenciamento de dados para aplicações de IA é relevante. O crescimento dos investimentos em Inteligência Artificial também aumenta a importância da infraestrutura necessária para sustentar essas soluções.

No caso da Startup Jarva's, essa relação é particularmente importante porque os documentos recebidos pela plataforma representam justamente a matéria-prima histórica que poderá ser utilizada para o treinamento e evolução dos futuros modelos de IA.

> **Toda essa evolução da IA depende de algo fundamental: dados bem armazenados, organizados, protegidos e disponíveis para utilização. Não existe IA de qualidade sem uma base de dados histórica adequada por trás.**

O projeto, portanto, representa um problema cada vez mais relevante:

> **Como construir uma infraestrutura capaz de transformar o crescimento da quantidade de dados em um ativo estratégico, sem comprometer segurança, disponibilidade e sustentabilidade financeira?**

<p align="center">
  <img width="1376" height="768" alt="Contexto de crescimento da IA" src="https://github.com/user-attachments/assets/cf38ec2f-b4db-4055-991c-67868188a3ac" />
</p>

---

# 2. Contextualização do Projeto

A **Startup Jarva's** é uma empresa em fase de hipercrescimento que oferece uma plataforma SaaS voltada para **extração inteligente de dados utilizando Inteligência Artificial**.

Como parte desse serviço, a plataforma recebe documentos enviados pelos clientes, principalmente **PDFs e imagens**, que servem como insumo para o processamento da IA.

O volume previsto é de aproximadamente **50 mil novos arquivos por mês**, equivalente a cerca de **600 mil arquivos por ano**, com tendência de crescimento contínuo.

O cenário possui uma característica que muda completamente a forma como o problema deve ser tratado:

> **Os arquivos não podem ser deletados.**

Os documentos antigos continuam tendo valor porque representam o histórico utilizado como base para o treinamento de futuros modelos de Inteligência Artificial.

Portanto, à medida que a empresa cresce, sua quantidade de dados também cresce continuamente.

Em poucos anos, a plataforma poderá acumular milhões de documentos. Esse histórico representa não apenas uma grande quantidade de dados, mas um ativo intelectual que pode contribuir diretamente para a evolução da empresa e de seus modelos de IA.

É justamente por isso que entendemos que a Startup Jarva's não está simplesmente construindo um repositório de documentos:

> **Um repositório preserva informações. Um ativo de dados preserva informações com a intenção de gerar valor a partir delas.**

Essa mudança de perspectiva é fundamental para compreender o restante do projeto. O armazenamento deixa de ser apenas uma infraestrutura de apoio e passa a fazer parte da própria estratégia do produto.

---

# 3. Problema a ser resolvido e impacto no negócio

O problema da Startup Jarva's é resultado da combinação de **crescimento acelerado, necessidade de isolamento entre clientes, retenção permanente dos documentos e controle dos custos de armazenamento**.

## 🔒 Segurança e isolamento dos dados

A plataforma possui natureza **multi-tenant**, ou seja, diferentes clientes utilizam a mesma aplicação e sua infraestrutura.

Isso cria uma necessidade fundamental:

> **Um cliente não pode ter acesso aos documentos pertencentes a outro cliente.**

Os usuários precisam conseguir acessar seus próprios documentos de maneira rápida e segura, mas sem que uma falha de configuração, permissão ou implementação permita que arquivos de outros usuários sejam expostos.

Essa necessidade de isolamento precisa ser considerada desde o início da arquitetura, e não tratada posteriormente como uma correção.

O risco associado a esse problema não é apenas teórico. O próprio documento de fundamentação do projeto utiliza um caso real como forma de contextualizar o impacto que uma configuração inadequada pode causar:

> ⚠️ Em 2022, um hacker alegou ter obtido dados de cerca de um bilhão de cidadãos chineses a partir de uma implantação do Elasticsearch associada a uma agência governamental. A própria reportagem levantou dúvidas sobre a veracidade e a dimensão da alegação, portanto o caso não deve ser tratado como uma exposição comprovada nessa escala.
>
> O exemplo é utilizado como contextualização do risco associado a configurações inadequadas de infraestrutura e exposição indevida de dados.

O valor do exemplo está em demonstrar o tipo de risco que a Startup Jarva's precisa evitar:

> **Uma configuração ou implantação inadequada pode transformar uma infraestrutura que deveria proteger dados em uma porta de acesso a eles.**

Isso é especialmente relevante para a Startup Jarva's porque a plataforma dependerá da confiança de clientes que estarão entregando seus próprios documentos ao serviço.

Uma exposição de dados comprometeria a confiança dos clientes na plataforma e, consequentemente, a própria proposta de valor da empresa. Por esse motivo:

> **Segurança não deve ser uma camada adicionada posteriormente. Ela precisa fazer parte da arquitetura desde o primeiro arquivo recebido pela plataforma.**

---

## 🗃️ Retenção dos documentos

Ao contrário de sistemas em que dados antigos podem ser descartados, a Startup Jarva's possui uma exigência estratégica diferente:

> **Nenhum arquivo deve ser excluído como parte da operação normal da plataforma.**

Os documentos representam a base histórica que poderá ser utilizada para o treinamento dos próximos modelos de IA. O fato de um documento ser antigo não significa que ele perdeu seu valor, pelo contrário, ele passa a fazer parte do patrimônio histórico de dados da empresa.

Em números, o cenário prevê aproximadamente **50 mil arquivos por mês**, o equivalente a cerca de **600 mil arquivos por ano**.

Como nenhum arquivo é descartado como parte da operação normal, esse volume continuará crescendo ao longo do tempo, podendo chegar a milhões de documentos após alguns anos de operação.

---

## 💵 Custo de armazenamento

A retenção permanente cria um segundo problema.

Se aproximadamente 50 mil arquivos são adicionados todos os meses e nenhum deles é removido, o volume armazenado continuará crescendo indefinidamente.

Manter todos esses documentos permanentemente em uma classe de armazenamento voltada para acesso frequente poderia gerar um custo incompatível com o crescimento da empresa.

Por isso, o projeto precisa considerar o **ciclo de vida dos dados**.

Documentos recentes possuem maior frequência de acesso e precisam de disponibilidade imediata, enquanto documentos históricos tendem a ser acessados com menor frequência, embora continuem tendo valor estratégico.

Na arquitetura proposta, os documentos permanecem inicialmente no **Amazon S3 Intelligent-Tiering**, adequado ao período de maior frequência de acesso.

Após os primeiros **12 meses**, uma regra de **S3 Lifecycle** pode realizar a transição automática dos objetos para o **S3 Glacier Deep Archive**, reduzindo o custo de armazenamento dos documentos históricos que continuam precisando ser preservados.

Essa estratégia permite que o custo de armazenamento acompanhe o comportamento esperado dos dados ao longo do tempo.

---

## ⚖️ O dilema central

A partir desses problemas, identificamos quatro necessidades que precisam ser atendidas simultaneamente:

1. **⚡ Acesso rápido:** os clientes precisam acessar normalmente os documentos durante os primeiros 12 meses.
2. **🗃️ Retenção permanente:** nenhum arquivo deve ser excluído como parte da operação normal da plataforma, pois todos fazem parte do ativo histórico da empresa.
3. **💵 Custo sob controle:** documentos antigos devem deixar de ocupar uma classe de armazenamento de acesso frequente quando o acesso se tornar menos frequente.
4. **🔒 Isolamento e segurança:** cada documento pertence a um cliente específico e não pode ser acessado por outros clientes.

É justamente a combinação dessas necessidades que torna o problema mais interessante.

A Startup Jarva's não pode simplesmente escolher a alternativa mais barata, porque isso poderia prejudicar o acesso aos documentos. Da mesma forma, não pode manter todo o histórico permanentemente em uma classe de armazenamento voltada para acesso frequente, porque o custo cresceria junto com a base histórica. E também não pode priorizar apenas a facilidade de acesso sem considerar o isolamento entre clientes.

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

### 🧱 Resiliência e tolerância a falhas

A solução deve evitar dependências em servidores ou componentes individuais cuja indisponibilidade possa interromper completamente o funcionamento da plataforma.

Sempre que possível, a arquitetura deve utilizar serviços gerenciados capazes de oferecer alta disponibilidade como parte de sua operação, reduzindo a necessidade de gerenciamento manual de infraestrutura.

Além disso, a solução deve ser capaz de continuar preservando os documentos e mantendo os principais serviços disponíveis mesmo diante de falhas pontuais de componentes ou da infraestrutura subjacente.

---

# 5. Solução

<details>
<summary><h3>🗂️ Índice rápido da Seção 5</h3></summary>

- 5.1 🧩 [Da necessidade à solução](#-da-necessidade-à-solução)
- 5.2 🔭 [Visão geral da solução](#-visão-geral-da-solução)
- 5.3 🛠️ [Serviços AWS utilizados](#-serviços-aws-utilizados)
- 5.4 🚶 [Jornada do Cliente](#-jornada-do-cliente)
- 5.5 🏗️ [Arquitetura AWS](#-arquitetura-aws)
- 5.6 🛡️ [Resiliência e tolerância a falhas](#resiliência-e-tolerância-a-falhas)
- 5.7 🧭 [Arquitetura, AWS CAF e AWS Well-Architected Framework](#-arquitetura-aws-caf-e-aws-well-architected-framework)
- 5.8 💰 [Custos do projeto](#-custos-do-projeto)
- 5.9 🚀 [Evolução e Visão de Futuro — Fase 02](#-evolução-e-visão-de-futuro--fase-02)

</details>

## 🧩 Da necessidade à solução

A partir desses requisitos, fica claro que o desafio da Startup Jarva's não está apenas em armazenar uma grande quantidade de documentos.

A arquitetura precisa acompanhar o crescimento da empresa, proteger os dados de cada cliente, preservar o histórico como um ativo estratégico e, ao mesmo tempo, manter os custos sob controle.

É a partir dessas necessidades que chegamos à proposta de arquitetura deste projeto.

A escolha dos serviços AWS não parte, portanto, da tecnologia em si, mas dos problemas que precisam ser resolvidos e dos requisitos que a solução precisa atender.

A proposta desenvolvida utiliza uma arquitetura **serverless**, baseada em serviços gerenciados da AWS, reduzindo a necessidade de gerenciamento de infraestrutura e permitindo que a solução acompanhe a demanda da plataforma.

A arquitetura também separa responsabilidades importantes do sistema:

- 🔑 Autenticação
- 🛂 Controle de acesso
- ⚙️ Lógica de negócio
- 🗄️ Armazenamento dos documentos
- 🏷️ Gerenciamento de metadados
- 👀 Observabilidade
- 📜 Auditoria
- ♻️ Gerenciamento do ciclo de vida dos dados
- 🧱 Provisionamento da infraestrutura

---

## 🔭 Visão geral da solução

A solução foi projetada para permitir que os clientes enviem e acessem seus documentos de forma segura, sem receber acesso direto ou irrestrito ao ambiente de armazenamento.

O fluxo começa com a autenticação do usuário pelo **Amazon Cognito**. Após a autenticação, as solicitações são direcionadas ao **Amazon API Gateway** e processadas pelo **AWS Lambda**, responsável por aplicar as regras de negócio e validar as permissões necessárias.

Os metadados e as informações de propriedade dos documentos são armazenados no **Amazon DynamoDB**, permitindo verificar se o usuário possui autorização para acessar determinado arquivo.

Os documentos são armazenados em um bucket privado do **Amazon S3**. Após a validação das permissões, o acesso é concedido por meio de **URLs pré-assinadas e temporárias**, limitadas à operação solicitada e a um período determinado.

Dessa forma, a solução contribui para o **isolamento entre clientes**, evita a exposição pública dos documentos e garante que cada usuário tenha acesso apenas aos arquivos para os quais possui autorização.

### 📤 Estratégia de acesso aos arquivos

Na Fase 01, os uploads e downloads são realizados diretamente com o **endpoint padrão do Amazon S3**, utilizando URLs pré-assinadas geradas pela aplicação.

Essa abordagem permite que o cliente transfira arquivos diretamente para o S3 sem que o conteúdo precise passar pelo API Gateway ou pelo AWS Lambda, reduzindo o processamento intermediário e mantendo o acesso controlado pela aplicação.

A utilização de URLs pré-assinadas garante que o usuário receba autorização apenas para realizar a operação específica solicitada e dentro de um período limitado.

Dessa forma, a arquitetura atende ao requisito de transferência segura dos documentos sem adicionar mecanismos adicionais de aceleração que não sejam necessários para o cenário atual.

### 📦 Estratégia de armazenamento

Durante os primeiros **12 meses**, os documentos permanecem no **Amazon S3 Intelligent-Tiering**, atendendo ao requisito de acesso frequente e disponibilidade imediata.

Após esse período, uma regra de **S3 Lifecycle** pode realizar a transição automática dos objetos para o **S3 Glacier Deep Archive**.

Essa classe é adequada ao armazenamento de longo prazo de dados que precisam ser preservados, mas que apresentam baixa frequência de acesso.

A transição permite reduzir o custo de armazenamento sem eliminar os documentos históricos.

### 🔏 Preservação dos documentos

O **S3 Object Lock** contribui para proteger os objetos contra exclusão ou alteração durante o período de retenção configurado.

A configuração da retenção deve ser definida de acordo com os requisitos de negócio da Startup Jarva's.

Dessa forma, o Object Lock funciona como uma camada adicional de proteção dos documentos, enquanto o S3 Lifecycle é responsável pela estratégia de transição entre classes de armazenamento.

### 🔑 Criptografia

Os objetos armazenados no Amazon S3 são protegidos por **criptografia server-side**, utilizando a criptografia padrão oferecida pelo serviço.

Em uma evolução futura, o **AWS KMS** poderá ser incorporado para proporcionar maior controle sobre as chaves criptográficas e suas respectivas políticas de acesso.

O resultado é uma arquitetura que busca equilibrar **segurança, escalabilidade, resiliência, preservação histórica, experiência do usuário e sustentabilidade dos custos**.

Ao utilizar serviços gerenciados e serverless, a solução também reduz a dependência de componentes individuais administrados pela equipe, beneficiando-se dos mecanismos de disponibilidade e tolerância a falhas oferecidos pelos serviços AWS utilizados.

---

## 🛠️ Serviços AWS utilizados

| Serviço | Papel na solução |
|---|---|
| 🔑 **Amazon Cognito** | Autenticação e gerenciamento da identidade dos usuários, incluindo a emissão de tokens JWT utilizados no controle de acesso à aplicação |
| 🚪 **Amazon API Gateway** | Camada de entrada da API, responsável pelo recebimento das solicitações, validação de autorização e integração com a lógica da aplicação |
| ⚙️ **AWS Lambda** | Execução da lógica de negócio, validação de identidade e permissões, consulta aos metadados e geração de URLs pré-assinadas |
| 🏷️ **Amazon DynamoDB** | Armazenamento dos metadados e informações de propriedade dos documentos, apoiando a validação de acesso e autorização |
| 🗄️ **Amazon S3 Intelligent-Tiering** | Classe de armazenamento utilizada para os documentos durante o período inicial de maior frequência de acesso, ajustando automaticamente as camadas de acesso conforme o padrão de utilização |
| ♻️ **S3 Lifecycle** | Gerenciamento do ciclo de vida dos documentos e transição automática dos objetos para classes de armazenamento mais adequadas ao longo do tempo |
| ❄️ **S3 Glacier Deep Archive** | Armazenamento histórico de longo prazo para documentos que precisam ser preservados, mas apresentam baixa frequência de acesso |
| 🔒 **S3 Object Lock** | Proteção dos objetos contra exclusão ou alteração durante o período de retenção configurado |
| 🛂 **AWS IAM** | Controle de permissões seguindo o princípio do menor privilégio entre os serviços e recursos da arquitetura |
| 📊 **Amazon CloudWatch** | Monitoramento operacional por meio de logs, métricas, dashboards e alarmes |
| 📜 **AWS CloudTrail** | Registro e auditoria das ações realizadas na conta e nos serviços AWS |
| 💰 **AWS Budgets** | Definição e acompanhamento de orçamentos, permitindo a criação de alertas relacionados aos custos da infraestrutura |
| 📈 **AWS Cost Explorer** | Análise dos custos e padrões de utilização dos serviços, apoiando a identificação de tendências e oportunidades de otimização |
| 🧱 **AWS CloudFormation** | Provisionamento, reprodução e padronização da infraestrutura por meio de código |
---

## 🚶 Jornada do Cliente

A arquitetura técnica mostra como os serviços se conectam. Entretanto, para compreender a solução sob a perspectiva de quem utiliza a plataforma, também desenvolvemos uma visão focada na **Jornada do Cliente**.

Essa jornada representa o caminho percorrido pelo usuário desde o acesso à plataforma até a preservação histórica de seus documentos.

<p align="center">
  <img width="1536" height="1024" alt="Jornada do Cliente - Plataforma SaaS de Gestão de Documentos com IA" src="https://github.com/user-attachments/assets/205a90b4-dfd8-44de-83bf-c4a7f09828fc" />
</p>

A jornada foi organizada em três momentos principais:

### 1. 📥 Acesso e envio

O cliente acessa a plataforma, realiza sua autenticação e envia um documento para o processamento da aplicação.

Nesse momento, o objetivo é proporcionar uma experiência simples ao usuário sem abrir mão da segurança e da identificação correta da propriedade do documento.

### 2. 🔐 Proteção e utilização

Após o envio, o documento é associado à conta do cliente e armazenado de forma segura.

Quando o usuário deseja consultar ou baixar um arquivo, a plataforma verifica sua identidade e suas permissões antes de liberar o acesso. O cliente não recebe acesso irrestrito ao ambiente de armazenamento. O acesso é concedido somente ao documento solicitado e de forma controlada.

### 3. 🗄️ Preservação histórica

Com o passar do tempo, os documentos continuam preservados como parte do histórico da empresa.

Durante os primeiros 12 meses, os arquivos permanecem em uma classe adequada ao acesso frequente. Após esse período, a estratégia de ciclo de vida permite realizar a transição para uma classe de armazenamento histórico de menor custo, mantendo os documentos preservados para futuras necessidades do negócio.

Essa visão reforça um dos princípios centrais do projeto:

> **A segurança e a preservação dos dados devem estar presentes durante toda a jornada do cliente, e não apenas no momento do armazenamento.**

---

## 🏗️ Arquitetura AWS

A visão técnica da solução apresenta os serviços AWS utilizados e o fluxo principal de comunicação entre os componentes da arquitetura.

<p align="center">
  <img width="1533" height="1026" alt="Image" src="https://github.com/user-attachments/assets/36705fb2-a173-4a72-9f50-2d1fefdc9bd7" />
</p>

### 🔍 Como a arquitetura resolve o problema?

A arquitetura foi projetada para responder diretamente aos principais desafios identificados pela Startup Jarva's.

- **🔒 Segurança e isolamento:** a autenticação pelo Amazon Cognito, as validações realizadas pela aplicação e o uso de URLs pré-assinadas permitem controlar o acesso aos documentos sem expor diretamente o ambiente de armazenamento.
- **🗃️ Retenção e preservação histórica:** o Amazon S3 oferece uma base durável para o armazenamento dos documentos, enquanto o S3 Object Lock contribui para protegê-los contra exclusões ou alterações durante o período de retenção definido.
- **📈 Crescimento e escalabilidade:** a utilização de serviços serverless e gerenciados permite que a solução acompanhe o aumento no número de usuários e documentos sem depender de servidores administrados individualmente pela equipe.
- **💰 Controle de custos:** o S3 Lifecycle permite adaptar o armazenamento ao ciclo de vida dos documentos, mantendo arquivos recentes disponíveis para acesso frequente e transferindo documentos históricos para classes de menor custo.
- **📤 Transferência controlada dos arquivos:** as URLs pré-assinadas permitem que os clientes realizem uploads e downloads diretamente no Amazon S3, sem receber permissões permanentes ou acesso irrestrito ao bucket.

Dessa forma, a arquitetura transforma os principais desafios do negócio em decisões técnicas, buscando equilibrar **segurança, acesso, preservação histórica, escalabilidade e sustentabilidade dos custos**.

### 🔁 Fluxo principal (requisição em tempo real)

O fluxo abaixo representa o caminho síncrono de uma requisição do usuário, do login até o armazenamento do documento:

1. O usuário realiza o login na plataforma utilizando o **Amazon Cognito**.
2. Após a autenticação, o usuário recebe os tokens necessários para acessar a aplicação.
3. As solicitações são enviadas para o **Amazon API Gateway**, que atua como ponto de entrada da API.
4. O **AWS Lambda** processa a solicitação e aplica as regras de negócio.
5. Quando necessário, a função consulta os metadados no **Amazon DynamoDB** para validar a propriedade e a autorização relacionadas ao documento.
6. Após a validação, a aplicação gera uma URL pré-assinada para a operação solicitada no **Amazon S3**.
7. O usuário realiza o upload ou download diretamente no S3 utilizando essa autorização temporária e o endpoint padrão do serviço.
8. Os documentos permanecem armazenados em um bucket privado.

A gestão do ciclo de vida dos documentos, incluindo a transição para o **S3 Glacier Deep Archive após 12 meses** e a proteção via **S3 Object Lock**, não faz parte desse fluxo síncrono. Esses mecanismos já foram detalhados nas seções [📦 Estratégia de armazenamento](#-estratégia-de-armazenamento) e [🔏 Preservação dos documentos](#-preservação-dos-documentos).

Além do fluxo principal, a arquitetura incorpora mecanismos de observabilidade, auditoria, controle de acesso, otimização de custos e infraestrutura como código.

---

## Resiliência e tolerância a falhas

Além de segurança e escalabilidade, a arquitetura também foi pensada para reduzir a dependência de componentes individuais que poderiam representar pontos únicos de falha.

Uma das principais decisões da Fase 01 foi utilizar uma arquitetura baseada em serviços **serverless e gerenciados pela AWS**. Isso significa que a equipe não precisa depender de um único servidor, máquina virtual ou instância para manter o funcionamento da aplicação.

Os principais componentes da solução, como **Amazon Cognito**, **Amazon API Gateway**, **AWS Lambda**, **Amazon DynamoDB** e **Amazon S3**, são serviços gerenciados que operam sobre uma infraestrutura fornecida pela AWS.

Dessa forma, a aplicação não depende de uma única Zona de Disponibilidade configurada manualmente pela equipe para executar seu fluxo principal. A responsabilidade pela infraestrutura subjacente e pela disponibilidade dos serviços é compartilhada com a AWS de acordo com as características e os acordos de nível de serviço de cada serviço.

### ⚠️ O que acontece se um componente falhar?

A arquitetura foi projetada para reduzir o impacto de falhas relacionadas à infraestrutura de componentes individuais. Por exemplo, não existe uma única instância EC2 responsável por processar todas as solicitações da plataforma.

A lógica da aplicação é executada pelo **AWS Lambda**, enquanto os documentos e metadados são armazenados em serviços gerenciados como **Amazon S3** e **Amazon DynamoDB**. Essa abordagem reduz o risco de que a falha de um único servidor administrado pela aplicação interrompa completamente o sistema.

Entretanto, é importante destacar que:

> **Resiliência não significa que a aplicação é imune a qualquer tipo de falha.**

Falhas relacionadas à lógica da aplicação, configurações incorretas, permissões inadequadas ou indisponibilidades de serviços externos ainda precisam ser consideradas durante a evolução do sistema.

Por esse motivo, a arquitetura incorpora mecanismos de **observabilidade**, utilizando o **Amazon CloudWatch**, e de **auditoria**, utilizando o **AWS CloudTrail**, permitindo identificar problemas e acompanhar o comportamento operacional da solução.

### 🌱 Resiliência como parte da evolução da arquitetura

A Fase 01 estabelece uma base resiliente por meio da utilização de serviços gerenciados e da redução de pontos únicos de falha sob responsabilidade direta da equipe.

Conforme a plataforma cresça e seus requisitos de disponibilidade se tornem mais exigentes, novos mecanismos poderão ser avaliados, como estratégias avançadas de recuperação, replicação de dados e planos de continuidade de negócio.

Dessa forma, a resiliência é tratada como um princípio presente desde a concepção da solução, mas também como uma área que pode evoluir de acordo com a criticidade e a escala do negócio.

---

## 🧭 Arquitetura, AWS CAF e AWS Well-Architected Framework

<p align="center">
  <img width="1376" height="768" alt="Image" src="https://github.com/user-attachments/assets/5ae1c337-4dae-42c0-8340-45ca05c827a4" />
</p>

A construção da solução foi orientada por boas práticas de arquitetura em nuvem, considerando princípios do [AWS Cloud Adoption Framework (AWS CAF)](https://aws.amazon.com/pt/cloud-adoption-framework/) e do [AWS Well-Architected Framework](https://aws.amazon.com/pt/architecture/well-architected/).

O AWS CAF ajuda a analisar a adoção da nuvem de forma ampla, relacionando a arquitetura às necessidades do negócio, à segurança, à operação e à gestão dos recursos. Já o AWS Well-Architected Framework oferece princípios técnicos para avaliar se a arquitetura está sendo construída de forma segura, confiável, eficiente e sustentável.

A relação da arquitetura com esses princípios pode ser resumida assim:

| Pilar | Foco | Serviços AWS envolvidos | Como contribui |
|---|---|---|---|
| 🔐 **Segurança** | Autenticação, controle de permissões e validação de propriedade dos documentos | Amazon Cognito, AWS IAM, Amazon API Gateway, AWS Lambda, URLs pré-assinadas, Amazon S3 (criptografia server-side) | Garante que o acesso aos dados seja controlado e limitado às operações autorizadas. Na Fase 02, o AWS KMS poderá ampliar o controle sobre as chaves criptográficas. |
| 🛡️ **Confiabilidade** | Reduzir a dependência de componentes individuais, garantir armazenamento durável e preservar o histórico de documentos | Amazon Cognito, Amazon API Gateway, AWS Lambda, Amazon DynamoDB, Amazon S3, S3 Lifecycle, S3 Glacier Deep Archive, S3 Object Lock, Amazon CloudWatch, infraestrutura como código | Apoia-se em infraestrutura gerenciada pela AWS, reduzindo pontos únicos de falha. Documentos ficam no Amazon S3 Intelligent-Tiering nos primeiros 12 meses e depois migram para o Glacier Deep Archive, reduzindo custos sem eliminá-los. O S3 Object Lock protege contra exclusão ou alteração durante a retenção, enquanto o CloudWatch monitora o comportamento operacional e a IaC garante reprodução consistente do ambiente. |
| ⚡ **Eficiência de performance** | Acompanhar a demanda sem depender de uma única máquina | Amazon API Gateway, AWS Lambda, Amazon DynamoDB, Amazon S3 | Serviços serverless e gerenciados oferecem uma base capaz de acompanhar o crescimento da aplicação. As transferências são realizadas diretamente com o Amazon S3 por meio de URLs pré-assinadas. |
| 💰 **Otimização de custos** | Adequar os recursos ao comportamento real da aplicação e ao padrão de acesso dos dados | S3 Lifecycle, S3 Glacier Deep Archive, serviços serverless | Documentos recentes ficam em classe de acesso frequente e migram para armazenamento histórico após 12 meses. A arquitetura evita adicionar serviços que não atendam a uma necessidade concreta do cenário atual. |
| 📊 **Excelência operacional** | Monitoramento, auditoria e reprodutibilidade da infraestrutura | Amazon CloudWatch, AWS CloudTrail, AWS CloudFormation | CloudWatch acompanha logs, métricas e alarmes; CloudTrail registra ações para auditoria e governança; CloudFormation permite provisionar e reproduzir a infraestrutura como código. |

---

## 💰 Custos do projeto

<p align="center">
  <img width="1376" height="768" alt="Estimativa de custos do projeto" src="https://github.com/user-attachments/assets/c5877632-d50d-452d-8545-5b1f6229f31a" />
</p>

A arquitetura foi projetada não apenas para atender aos requisitos técnicos da Startup Jarva's, mas também para manter os custos compatíveis com o crescimento da plataforma.

Considerando um cenário de aproximadamente **50.000 novos documentos por mês**, a estimativa da Fase 01 resulta em:

| Indicador | Estimativa |
|---|---:|
| 💵 **Custo mensal recorrente** | **US$ 143,54** |
| 🧾 **Custo inicial** | **US$ 33,00** |
| 📅 **Projeção em 12 meses** | **US$ 1.755,48** |
| 📄 **Custo por documento/mês** | **US$ 0,0029** |

> 💡 **Em outras palavras:** a arquitetura consegue processar aproximadamente **50 mil documentos por mês** com um custo recorrente inferior a **US$ 0,003 por documento**, demonstrando um baixo custo marginal por unidade processada.

### 📊 Onde está concentrado o custo?

A maior parte do custo está relacionada ao **armazenamento e à transferência dos documentos**, e não à capacidade computacional.

- 🗄️ **Amazon S3 Intelligent-Tiering:** US$ 65,63/mês
- 🌐 **Transferência de dados:** US$ 61,44/mês
- ❄️ **S3 Glacier Deep Archive:** US$ 8,42/mês
- 📊 **Amazon CloudWatch:** US$ 6,18/mês
- ⚙️ **Demais serviços:** impacto inferior a 1% ou custo estimado de US$ 0,00 na escala analisada

Essa distribuição reforça uma das principais decisões arquiteturais do projeto: **o custo deve acompanhar o ciclo de vida e o comportamento dos dados**.

Documentos recentes permanecem em uma camada adequada ao acesso frequente, enquanto documentos históricos podem ser direcionados para armazenamento de longo prazo e menor custo.

### 📈 Estratégia de otimização

A arquitetura evita adicionar serviços ou mecanismos de otimização sem uma necessidade concreta.

Um exemplo é o **S3 Transfer Acceleration**. Embora possa melhorar a experiência de transferência em cenários de expansão geográfica, sua adoção aumentaria significativamente os custos estimados. Por isso, foi mantido como uma possibilidade de evolução da **Fase 02**, e não como componente obrigatório da Fase 01.

> **A estratégia adotada é simples: adicionar complexidade e custo somente quando o crescimento real da plataforma justificar o investimento.**

### 📄 Detalhamento da precificação

A estimativa completa, incluindo as premissas utilizadas, cálculo das leituras, custos por serviço, projeção de 12 meses, níveis de gratuidade e análise do impacto do S3 Transfer Acceleration, está disponível no documento:

👉 **[📄 Precificação Serviços AWS - Startup Jarva's](./Precificação%20Serviços%20AWS%20-%20Startup%20Jarva's.md)**

> *Estimativa elaborada com base na AWS Pricing Calculator, utilizando a região Leste dos EUA (N. da Virgínia). Os valores representam uma projeção baseada nas premissas do cenário e podem variar conforme o comportamento real da aplicação e alterações nos preços dos serviços AWS.*

---

## 🚀 Evolução e Visão de Futuro — Fase 02

A arquitetura apresentada na Fase 01 foi desenvolvida para atender aos principais requisitos do cenário proposto, priorizando segurança, isolamento entre clientes, escalabilidade, resiliência, retenção dos documentos, otimização de custos, observabilidade e reprodutibilidade da infraestrutura.

Como parte da evolução da solução, identificamos alguns pontos que podem ser aprimorados em uma segunda fase do projeto.

Essas melhorias não são necessárias para que a arquitetura inicial atenda aos requisitos definidos, mas representam oportunidades para elevar o nível de segurança, governança, resiliência, performance e maturidade operacional da plataforma conforme o negócio cresça.

A Fase 02 não representa uma substituição da arquitetura atual. Ela parte da base construída na Fase 01 e avalia quais novos recursos e estratégias passam a fazer sentido à medida que aumentam o número de usuários, o volume de documentos, a criticidade da operação e a sensibilidade dos dados armazenados.

### 🔐 Fase 02 — Evolução da Segurança e Governança

A Fase 02 tem como principal objetivo fortalecer a proteção dos dados e o gerenciamento de informações sensíveis, complementando os mecanismos de segurança já presentes na Fase 01.

Os serviços avaliados para esta etapa são:

| Serviço | Objetivo na Fase 02 |
|---|---|
| 🔑 **AWS KMS** | Gerenciamento centralizado de chaves criptográficas e maior controle sobre a proteção dos dados |
| 🤫 **AWS Secrets Manager** | Armazenamento e gerenciamento seguro de credenciais, segredos e informações sensíveis utilizadas pela aplicação |
| 🔎 **Amazon Macie** | Descoberta e identificação de dados sensíveis armazenados no Amazon S3, apoiando a classificação e a proteção das informações |

A adoção desses serviços deve ser avaliada considerando o crescimento da plataforma, o nível de sensibilidade dos documentos armazenados e o impacto financeiro de sua utilização.

Cada recurso deve ser incorporado quando houver uma necessidade concreta que justifique seu uso, considerando segurança, governança, complexidade operacional e custo, e não como forma de simplesmente aumentar a quantidade de componentes da arquitetura.

### ⚡ Fase 02 — Evolução de Performance e Experiência Global

A Fase 01 utiliza o endpoint padrão do Amazon S3 para realizar as transferências de arquivos, uma vez que o cenário inicial não estabelece a distância geográfica como um problema ou requisito obrigatório da solução.

Entretanto, conforme a Startup Jarva's cresça, o comportamento das transferências poderá ser acompanhado para identificar possíveis impactos relacionados à localização dos usuários, ao tamanho dos arquivos e à experiência de upload e download.

Nesse contexto, o **S3 Transfer Acceleration** poderá ser avaliado como uma possível evolução da arquitetura.

Sua adoção faria mais sentido em um cenário como:

- 🌎 expansão internacional da plataforma;
- 📍 clientes distribuídos geograficamente em regiões distantes do bucket;
- 📦 aumento significativo do tamanho dos arquivos transferidos;
- 📈 crescimento expressivo no volume de transferências;
- 📊 identificação, por meio de métricas ou feedback dos usuários, de degradação na experiência causada pela distância geográfica.

Dessa forma, o serviço deixa de ser tratado como um componente obrigatório da arquitetura e passa a representar uma **decisão orientada pela necessidade real de performance**.

> **O objetivo não é adicionar mecanismos de otimização antecipadamente, mas avaliar sua adoção quando os dados da operação demonstrarem que o benefício justifica o custo adicional.**

Essa abordagem mantém a Fase 01 mais alinhada ao cenário atual e permite que a arquitetura evolua de forma progressiva conforme novos requisitos surjam.

### 🚀 Como a solução pode evoluir?

A evolução da plataforma pode ser analisada a partir de algumas perguntas importantes:

- Como a solução poderia atender a um volume significativamente maior de usuários e documentos?
- Como aumentar o nível de proteção dos dados conforme a quantidade e a sensibilidade das informações cresçam?
- Como identificar e monitorar automaticamente a presença de informações sensíveis nos documentos armazenados?
- Como melhorar o gerenciamento de credenciais e informações confidenciais utilizadas pela aplicação?
- Como aumentar o controle sobre as chaves utilizadas para proteger os dados?
- Como reduzir ainda mais o impacto de falhas e indisponibilidades em componentes críticos da solução?
- Como estabelecer estratégias de recuperação e continuidade caso os requisitos de disponibilidade da plataforma se tornem mais rigorosos?
- Como manter uma boa experiência de transferência caso a plataforma passe a atender clientes distribuídos globalmente?
- Como manter o crescimento da plataforma sustentável sem aumentar os custos de forma desproporcional?

A Fase 02 representa, portanto, uma evolução natural da arquitetura, na qual mecanismos adicionais de segurança, governança, performance e resiliência podem ser incorporados conforme as necessidades do negócio se tornem mais complexas.

### 📈 Visão de futuro

Em um cenário de crescimento da Startup Jarva's, a arquitetura poderá evoluir para atender a um volume maior de usuários, documentos e processamento, mantendo os princípios que orientaram a solução desde sua concepção.

Entre as possibilidades de evolução estão:

- **🔑 Maior proteção criptográfica:** utilização do AWS KMS para ampliar o controle sobre as chaves criptográficas e os mecanismos de proteção dos dados.
- **🤫 Gestão de informações sensíveis:** utilização do AWS Secrets Manager para centralizar e proteger credenciais e outros segredos utilizados pela aplicação.
- **🔎 Descoberta de dados sensíveis:** utilização do Amazon Macie para identificar e classificar informações potencialmente sensíveis armazenadas no Amazon S3.
- **⚡ Evolução da performance global:** avaliação do S3 Transfer Acceleration caso a expansão geográfica da plataforma ou o comportamento real das transferências justifique o investimento adicional.
- **🛡️ Maior resiliência:** avaliação de mecanismos adicionais de recuperação e continuidade de negócio conforme os requisitos de disponibilidade e criticidade da plataforma aumentem.
- **📜 Maior governança:** ampliação dos mecanismos de auditoria, monitoramento e controle conforme a plataforma cresça.
- **📈 Escalabilidade:** evolução da arquitetura para suportar um aumento significativo no número de usuários e documentos sem depender de componentes individuais que limitem o crescimento.
- **💰 Otimização de custos:** revisão contínua das estratégias de armazenamento e utilização dos serviços conforme o comportamento real da aplicação.

Essas melhorias não precisam necessariamente ser implementadas na primeira versão da solução. O objetivo desta etapa é demonstrar que a arquitetura foi pensada não apenas para atender ao cenário atual, mas também para permitir uma evolução consistente conforme o negócio cresça.

> **A Fase 01 resolve o problema atual. A Fase 02 prepara a arquitetura para os desafios que surgem com o crescimento e a maturidade da plataforma.**

---

# 6. Como o projeto foi desenvolvido

<p align="center">
  <img width="1905" height="1065" alt="Fluxo de gestão ágil do projeto" src="https://github.com/user-attachments/assets/9b9cb4cf-11d1-4d90-8950-c318547d43de" />
</p>

O desenvolvimento do projeto foi conduzido a partir de uma abordagem de **gestão ágil**, combinando **Scrum**, **Kanban** e **PDCA** para organizar as atividades, acompanhar a evolução da solução e promover ciclos contínuos de análise, desenvolvimento e revisão.

Como o projeto envolvia não apenas a construção de uma arquitetura técnica, mas também a análise do problema de negócio, o levantamento de requisitos, a avaliação de serviços AWS e a elaboração da documentação, cada uma dessas práticas contribuiu para uma dimensão diferente do processo.

## 🏃 Sprints semanais (Scrum)

O trabalho foi organizado em **Sprints semanais**, nas quais eram definidos os principais objetivos do ciclo. Reuniões periódicas acompanhavam o andamento das tarefas, discutiam dificuldades, alinhavam decisões e revisavam entregas.

Essa organização permitiu dividir um problema inicialmente amplo em entregas menores e progressivas: em vez de definir toda a arquitetura de uma só vez, as decisões foram amadurecidas conforme a equipe aprofundava sua compreensão do problema, dos requisitos e das possibilidades oferecidas pelos serviços AWS.

## 🗂️ Quadro Kanban

O fluxo de trabalho foi visualizado em um **quadro Kanban no Trello**, com as atividades organizadas em etapas — **To Do, In Progress, In Review e Done**. O quadro também centralizava anotações de contextualização, planejamento e sugestões, dando à equipe uma visão compartilhada do que precisava ser feito, do que estava em andamento e do que já havia sido concluído.

## 🔄 PDCA e melhoria contínua

De forma complementar às Sprints, aplicamos o ciclo **PDCA (Plan, Do, Check, Act)** para avaliar e aprimorar continuamente as decisões:

1. **Plan:** identificar prioridades e definir os objetivos do ciclo.
2. **Do:** executar as atividades planejadas.
3. **Check:** revisar resultados e decisões, identificando pontos de melhoria.
4. **Act:** incorporar os aprendizados, ajustando o planejamento seguinte.

Esse ciclo foi essencial porque várias decisões arquiteturais amadureceram ao longo do projeto: à medida que a análise dos requisitos avançava, novas necessidades e oportunidades de melhoria eram identificadas e incorporadas.

## 🔗 Como as abordagens se conectam

**Scrum** deu estrutura aos ciclos de trabalho, **Kanban** trouxe visibilidade ao fluxo das atividades, e **PDCA** garantiu a avaliação e melhoria contínua do processo:

**Planejamento → Sprint → Execução → Revisão → Ajustes → Próxima Sprint**

Essa combinação equilibrou organização e flexibilidade — havia objetivos claros para cada ciclo, mas também espaço para revisar decisões conforme novos aspectos do problema surgiam.

## 🧭 Gestão das decisões e evolução da arquitetura

As decisões não foram tratadas como tarefas técnicas isoladas: cada escolha foi relacionada aos requisitos do projeto, às necessidades do negócio e a aspectos como **segurança, escalabilidade, resiliência, disponibilidade, retenção e custos**. A evolução seguiu um fluxo progressivo:

**Entendimento do problema → Levantamento de requisitos → Análise de alternativas → Definição da solução → Revisão → Evolução da arquitetura**

Esse processo também permitiu distinguir o que era necessário para atender aos requisitos da **Fase 01** daquilo que poderia ser incorporado depois, como parte da evolução da plataforma.

Um exemplo desse processo foi a análise do **S3 Transfer Acceleration**. Inicialmente considerado como uma alternativa para otimizar a transferência dos arquivos, o serviço foi reavaliado a partir dos requisitos reais do cenário e do impacto sobre os custos da solução. Como não havia um requisito relacionado à transferência global ou evidências de problemas de performance causados pela distância geográfica, optamos por manter a Fase 01 utilizando o endpoint padrão do Amazon S3 e URLs pré-assinadas.

Recursos como **AWS KMS, AWS Secrets Manager, Amazon Macie** e mecanismos adicionais de otimização de performance foram reservados para possíveis evoluções futuras, evitando adicionar complexidade e custo à arquitetura inicial sem uma necessidade concreta que os justificasse.

## ✅ Resultado da abordagem de gestão

A combinação de **Scrum, Kanban e PDCA** permitiu que a equipe acompanhasse a evolução da solução, revisasse decisões e incorporasse melhorias de forma incremental e colaborativa — resultando em um processo no qual **gestão e arquitetura evoluíram juntas**.

> **O projeto não foi desenvolvido como uma sequência linear de decisões. Ele evoluiu em ciclos de planejamento, execução, revisão e melhoria contínua, permitindo que a solução amadurecesse junto com o entendimento do problema.**

---

# 7. Infraestrutura como Código

A infraestrutura da solução foi desenvolvida seguindo o conceito de **Infrastructure as Code (IaC)**, permitindo que os recursos necessários para a arquitetura sejam definidos e provisionados por meio de código.

Essa abordagem contribui para que a infraestrutura seja **reproduzível, consistente e versionável**, reduzindo a dependência de configurações manuais e facilitando a criação de ambientes com a mesma estrutura arquitetural.

Para este projeto, a infraestrutura foi implementada utilizando o **AWS CloudFormation**, por meio de um template que descreve os recursos e suas configurações. O desenvolvimento do modelo também considerou as [práticas recomendadas oficiais da AWS](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/best-practices.html), incluindo aspectos relacionados à criação de templates, ao gerenciamento de pilhas e ao controle de acesso por meio do AWS IAM.

Dessa forma, a arquitetura deixa de existir apenas como um diagrama conceitual e passa a poder ser representada e provisionada de forma estruturada por meio de código.

### 🔗 Acesse o código da infraestrutura

[![Ver infrastructure.yaml](https://img.shields.io/badge/CloudFormation-infrastructure.yaml-527FFF?style=for-the-badge&logo=amazonaws&logoColor=white)](https://github.com/lbarretto/jarvas-aws-architecture/blob/main/infrastructure.yaml)

---
# 8. 🎬 Vídeo de Apresentação

Para complementar a documentação escrita, gravamos um vídeo de apresentação do projeto, no qual explicamos o contexto do desafio, os principais problemas identificados e a arquitetura da solução proposta.

<div align="center">

[![Assista ao vídeo de apresentação](https://img.shields.io/badge/▶️-Assistir%20no%20YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://youtu.be/4kUy7GKyM3A)

</div>

---

# 9. Agradecimentos

Este projeto foi construído de forma colaborativa como parte de uma jornada de aprendizado e aplicação prática dos conhecimentos adquiridos durante a preparação em computação em nuvem.

Agradecemos à **Escola da Nuvem**, aos professores, mentores e a todos os integrantes da equipe que contribuíram com análises, ideias e diferentes perspectivas ao longo do desenvolvimento do projeto.

<p align="center">
  <em><img width="1196" height="892" alt="Image" src="https://github.com/user-attachments/assets/7d9b668e-a836-4cfd-a797-54402378410d" /></em>
</p>

---

# 10. Referências

**1. Amazon S3 — Block Public Access**
Configurações de bloqueio de acesso público e como essas configurações podem impedir políticas ou permissões que permitiriam acesso público aos objetos.

**2. Amazon S3 — URLs pré-assinadas**
Documentação oficial sobre URLs pré-assinadas e como conceder acesso temporário e controlado a objetos armazenados no Amazon S3.

**3. AWS re:Post — Acesso por prefixo**
Exemplo oficial de política de IAM que utiliza a condição `s3:prefix` e variáveis de identidade para restringir usuários aos seus próprios prefixos dentro de um bucket compartilhado.

**4. Amazon S3 — Gerenciamento do ciclo de vida de objetos**
Documentação oficial sobre regras de S3 Lifecycle e transição de objetos entre diferentes classes de armazenamento, incluindo cenários de armazenamento histórico e de longo prazo.

**5. Amazon API Gateway — Features**
Documentação sobre o papel do API Gateway como camada de publicação de APIs, integração com AWS Lambda, controle de tráfego e recursos de segurança e monitoramento.

**6. AWS Lambda**
Documentação oficial sobre o modelo de execução serverless, execução orientada a eventos, integração com outros serviços AWS e cobrança baseada no uso.

**7. G1 Tecnologia — Reportagem jornalística**
Caso da Polícia de Xangai (2022): alegação de exposição de registros associados a cerca de 1 bilhão de cidadãos por uma possível falha de configuração em uma infraestrutura de dados.

O caso é utilizado exclusivamente como contextualização do risco relacionado à exposição indevida de dados e não como comprovação técnica de uma exposição nessa escala.

**8. IBM — Cost of a Data Breach Report 2026**
Relatório anual da IBM sobre custos, causas e impactos relacionados a violações de dados, utilizado como referência para contextualizar os riscos associados à segurança de informações e à evolução da Inteligência Artificial.

**9. Gartner — Worldwide AI Spending**
Projeções da Gartner sobre o crescimento dos investimentos globais em Inteligência Artificial e a importância crescente da infraestrutura necessária para suportar essas soluções.

---

<div align="center">

**☁️ Startup Jarva's**
Plataforma SaaS de Gestão de Documentos com IA

[![Voltar ao topo](https://img.shields.io/badge/⬆-Voltar%20ao%20topo-lightgrey?style=flat-square)](#-startup-jarvas)

</div>
