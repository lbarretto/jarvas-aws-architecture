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
  - [Arquitetura, AWS CAF e AWS Well-Architected Framework](#arquitetura-aws-caf-e-aws-well-architected-framework)
  - [Custos do projeto](#custos-do-projeto)
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

No cenário proposto, os documentos enviados pelos clientes não são apenas arquivos que precisam ser armazenados. Eles representam a base histórica utilizada para a evolução futura dos modelos de IA da empresa. Assim, garantir que esses dados estejam organizados, protegidos, disponíveis quando necessários e economicamente sustentáveis ao longo do tempo é parte fundamental da estratégia do negócio.

Além disso, o cenário proposto está inserido em um contexto de crescimento significativo do mercado de Inteligência Artificial. Como identificado durante a análise do cenário:

> Segundo projeção da consultoria Gartner, o investimento global em inteligência artificial deve alcançar US$ 2,59 trilhões em 2026, alta de 47% em relação ao ano anterior, com expectativa de chegar a quase US$ 3,5 trilhões em 2027.
>
> No Brasil, um estudo da IBM mostrou que 78% das empresas nacionais planejam ampliar seus investimentos em IA, e os gastos com IA no país devem ultrapassar US$ 2,4 bilhões, crescimento de 30% em relação a 2024.
>
> A adoção estratégica também disparou: 95,2% das organizações consideram a IA uma prioridade estratégica para 2026, contra apenas 32,8% que investiam na tecnologia em 2024.
>
> Cerca de 45% de todo o investimento previsto para 2026 vai para infraestrutura de IA — aproximadamente US$ 1,4 trilhão — incluindo justamente os componentes que estou utilizando: armazenamento em nuvem, processamento serverless e pipelines de dados.

Esses dados ajudam a contextualizar por que uma arquitetura voltada ao armazenamento e gerenciamento de dados para aplicações de IA é relevante. O crescimento dos investimentos em Inteligência Artificial também aumenta a importância da infraestrutura necessária para sustentar essas soluções.

No caso da Startup XYZ, essa relação é particularmente importante porque os documentos recebidos pela plataforma representam justamente a matéria-prima histórica que poderá ser utilizada para o treinamento e evolução dos futuros modelos de IA.

> Toda essa onda de investimento em IA depende de algo que raramente aparece nas manchetes: dados bem armazenados, organizados e disponíveis para treinar modelos. Não existe IA de qualidade sem uma base de dados histórica bem estruturada por trás. O case da Startup XYZ é, na prática, uma versão em escala reduzida desse problema que empresas de todos os portes estão enfrentando agora — e é isso que pretendo deixar claro logo na abertura da apresentação.

Portanto, o projeto não foi escolhido apenas por envolver serviços populares de computação em nuvem ou Inteligência Artificial. Ele representa um problema cada vez mais relevante: **como construir uma infraestrutura capaz de transformar o crescimento da quantidade de dados em um ativo estratégico, sem comprometer segurança, disponibilidade e sustentabilidade financeira.**

---

# 2. Contextualização do Projeto

A **Startup XYZ** é uma empresa em fase de hipercrescimento que oferece uma plataforma SaaS voltada para **extração inteligente de dados utilizando Inteligência Artificial**.

Como parte desse serviço, a plataforma recebe documentos enviados pelos clientes, principalmente **PDFs e imagens**, que servem como insumo para o processamento da IA.

O volume previsto é de aproximadamente **50 mil novos arquivos por mês**, equivalente a cerca de **600 mil arquivos por ano**, com tendência de crescimento contínuo.

À primeira vista, o problema poderia parecer simplesmente uma questão de armazenamento. Entretanto, o cenário possui uma característica que muda completamente a forma como o problema deve ser tratado: **os arquivos não podem ser deletados**.

Os documentos antigos continuam tendo valor porque representam o histórico utilizado como base para o treinamento de futuros modelos de Inteligência Artificial. Portanto, à medida que a empresa cresce, sua quantidade de dados também cresce continuamente.

Em poucos anos, a plataforma poderá acumular milhões de documentos. Esse histórico representa não apenas uma grande quantidade de dados, mas um ativo intelectual que pode contribuir diretamente para a evolução da empresa e de seus modelos de IA.

É justamente por isso que entendemos que a Startup XYZ não está simplesmente construindo um repositório de documentos.

> **Um repositório preserva informações. Um ativo de dados preserva informações com a intenção de gerar valor a partir delas.**

Essa mudança de perspectiva é fundamental para compreender o restante do projeto. O armazenamento deixa de ser apenas uma infraestrutura de apoio e passa a fazer parte da própria estratégia do produto.

---

# 3. Problema a ser resolvido e impacto no negócio

O problema da Startup XYZ é resultado da combinação de **crescimento acelerado, necessidade de isolamento entre clientes, retenção permanente dos documentos e controle dos custos de armazenamento**.

## Segurança e isolamento dos dados

A plataforma possui natureza **multi-tenant**, ou seja, diferentes clientes utilizam a mesma aplicação e sua infraestrutura.

Isso cria uma necessidade fundamental: **um cliente não pode ter acesso aos documentos pertencentes a outro cliente**.

Os usuários precisam conseguir acessar seus próprios documentos de maneira rápida e segura, mas sem que uma falha de configuração, permissão ou implementação permita que arquivos de outros usuários sejam expostos.

Essa necessidade de isolamento precisa ser considerada desde o início da arquitetura, e não tratada posteriormente como uma correção.

O risco associado a esse problema não é apenas teórico. O próprio documento de fundamentação do projeto utiliza um caso real como forma de contextualizar o impacto que uma configuração inadequada pode causar:

> Em 2022, um hacker alegou ter obtido dados de cerca de um bilhão de cidadãos chineses a partir de uma implantação
> do Elasticsearch associada a uma agência governamental. A própria reportagem do G1 levantou dúvidas sobre a
> veracidade e a dimensão da alegação, portanto o caso não deve ser tratado como uma exposição comprovada nessa
> escala.
> Fonte: G1 Tecnologia, "Hacker alega ter roubado da polícia registros de 1 bilhão de chineses" (jul. 2022) — g1.globo.com/tecnologia

O ponto principal, entretanto, não é afirmar que esse caso representa uma exposição comprovada naquela escala. O valor do exemplo está em demonstrar o tipo de risco que a Startup XYZ precisa evitar: **uma configuração ou implantação inadequada pode transformar uma infraestrutura que deveria proteger dados em uma porta de acesso a eles.**

Isso é especialmente relevante para a Startup XYZ porque a plataforma dependerá da confiança de clientes que estarão entregando seus próprios documentos ao serviço.

Uma exposição de dados, portanto, não seria apenas um incidente técnico. Ela poderia comprometer a confiança dos clientes na plataforma e, consequentemente, a própria proposta de valor da empresa.

Por esse motivo, **segurança não deve ser uma camada adicionada posteriormente**. Ela precisa fazer parte da arquitetura desde o primeiro arquivo recebido pela plataforma.

---

## Retenção dos documentos

Ao contrário de sistemas em que dados antigos podem ser descartados, a Startup XYZ possui uma exigência estratégica diferente:

**nenhum arquivo deve ser deletado.**

Os documentos representam a base histórica que poderá ser utilizada para o treinamento dos próximos modelos de IA. Dessa forma, o fato de um documento ser antigo não significa que ele perdeu seu valor. Pelo contrário, ele passa a fazer parte do patrimônio histórico de dados da empresa.

Em números, o cenário prevê aproximadamente **50 mil arquivos por mês**, o equivalente a cerca de **600 mil arquivos por ano**. Como nenhum arquivo é descartado, esse volume continuará crescendo ao longo do tempo, podendo chegar a milhões de documentos após alguns anos de operação.

---

## Custo de armazenamento

A retenção permanente cria um segundo problema.

Se aproximadamente 50 mil arquivos são adicionados todos os meses e nenhum deles é removido, o volume armazenado continuará crescendo indefinidamente.

Manter todos esses documentos permanentemente em uma camada de armazenamento voltada para acesso frequente poderia gerar um custo incompatível com o crescimento da empresa.

Por isso, o projeto precisa considerar o **ciclo de vida dos dados**. Documentos recentes possuem maior frequência de acesso e precisam de disponibilidade imediata, enquanto documentos históricos tendem a ser acessados com menor frequência, embora continuem tendo valor estratégico.

Essa diferença permite pensar no armazenamento não como um único espaço estático, mas como uma estrutura em que **o custo acompanha o comportamento do dado ao longo do tempo**.

---

## O dilema central

A partir desses problemas, identificamos quatro necessidades que precisam ser atendidas simultaneamente:

1. **Acesso rápido:** os clientes precisam acessar normalmente os documentos durante os primeiros 12 meses.
2. **Retenção permanente:** nenhum arquivo pode ser deletado, pois todos fazem parte do ativo histórico da empresa.
3. **Custo sob controle:** documentos antigos precisam deixar de ocupar uma camada de armazenamento mais cara quando o acesso se tornar menos frequente.
4. **Isolamento e segurança:** cada documento pertence a um cliente específico e não pode ser acessado por outros clientes.

É justamente a combinação dessas necessidades que torna o problema mais interessante.

A Startup XYZ não pode simplesmente escolher a alternativa mais barata, porque isso poderia prejudicar o acesso aos documentos. Da mesma forma, não pode manter todos os dados permanentemente na camada de maior disponibilidade, porque o custo cresceria junto com a base histórica.

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

Os documentos históricos não devem ser excluídos pela aplicação.

A solução deve permitir que os arquivos permaneçam preservados mesmo quando deixarem de ser acessados com frequência.

### ⚡ Disponibilidade e acesso

Os documentos enviados pelos clientes devem permanecer disponíveis para consulta durante o período em que apresentam maior frequência de acesso, especialmente durante os primeiros 12 meses.

### 💰 Economia

O custo de armazenamento deve ser reduzido conforme os documentos envelhecem.

A solução deve permitir que os arquivos continuem preservados sem exigir que todo o histórico permaneça permanentemente em uma camada de armazenamento de acesso frequente.

### 📊 Operação e acompanhamento

A infraestrutura deve permitir acompanhar o funcionamento da solução, identificar falhas e manter uma trilha de auditoria das ações realizadas.

### 🔄 Reprodutibilidade

A infraestrutura deve poder ser recriada de forma consistente, permitindo que a arquitetura seja documentada e reproduzida por meio de código.

---

# 5. Solução

## Da necessidade à solução

A partir desses requisitos, fica claro que o desafio da Startup XYZ não está apenas em armazenar uma grande quantidade de documentos. A arquitetura precisa acompanhar o crescimento da empresa, proteger os dados de cada cliente, preservar o histórico como um ativo estratégico e, ao mesmo tempo, manter os custos sob controle.

É a partir dessas necessidades que chegamos à proposta de arquitetura deste projeto. A escolha dos serviços AWS não parte, portanto, da tecnologia em si, mas dos problemas que precisam ser resolvidos e dos requisitos que a solução precisa atender.

A proposta desenvolvida utiliza uma arquitetura **serverless**, baseada em serviços gerenciados da AWS, reduzindo a necessidade de gerenciamento de infraestrutura e permitindo que a solução acompanhe a demanda da plataforma.

A arquitetura também separa responsabilidades importantes do sistema: autenticação, controle de acesso, lógica de negócio, armazenamento dos documentos, gerenciamento de metadados, observabilidade, auditoria e provisionamento da infraestrutura.

## Visão geral da solução

A solução foi projetada para que o cliente possa enviar e acessar documentos sem receber acesso direto e irrestrito ao ambiente de armazenamento.

O fluxo começa com a autenticação do usuário por meio do **Amazon Cognito**. Após a autenticação, a aplicação utiliza o token de identidade para realizar solicitações à API, publicada pelo **Amazon API Gateway**.

As solicitações são encaminhadas para funções do **AWS Lambda**, responsáveis por aplicar as regras de negócio e validar se o usuário possui autorização para realizar determinada operação.

Os metadados dos documentos e as informações de propriedade são armazenados no **Amazon DynamoDB**. Dessa forma, antes de permitir operações como consulta, download ou geração de uma URL de acesso, a aplicação pode verificar a relação entre o usuário autenticado e o documento solicitado.

Os arquivos são armazenados em um bucket privado do **Amazon S3**, organizado de acordo com a estrutura definida pela aplicação. O acesso aos objetos ocorre por meio de URLs pré-assinadas e temporárias, geradas somente após a validação das permissões necessárias.

Essa abordagem contribui para o isolamento entre clientes e evita a exposição pública do bucket. O usuário recebe autorização apenas para realizar a operação específica solicitada e dentro de um período limitado.

Para acompanhar o crescimento da base histórica, a solução também utiliza recursos de gerenciamento do ciclo de vida dos dados. Os documentos podem permanecer inicialmente em uma camada adequada ao seu padrão de acesso e, após o período definido pela estratégia de retenção, são movimentados automaticamente para uma camada de armazenamento histórico de menor custo.

Ao mesmo tempo, o **S3 Object Lock** contribui para a preservação dos documentos durante o período de retenção configurado, reforçando o requisito de que o histórico não seja removido ou alterado indevidamente.

O resultado é uma arquitetura que busca equilibrar **segurança, escalabilidade, preservação histórica, experiência do usuário e sustentabilidade dos custos**.

---

## Serviços AWS utilizados

| Serviço | Papel na solução |
|---|---|
| **Amazon Cognito** | Autenticação e gerenciamento da identidade dos usuários |
| **Amazon API Gateway** | Camada de entrada da API, validação de solicitações e integração com a lógica da aplicação |
| **AWS Lambda** | Execução da lógica de negócio, validações e geração de URLs pré-assinadas |
| **Amazon DynamoDB** | Armazenamento dos metadados e informações de propriedade dos documentos |
| **Amazon S3** | Armazenamento seguro e durável dos documentos |
| **S3 Intelligent-Tiering** | Otimização automática da camada de armazenamento de acordo com o padrão de acesso |
| **S3 Lifecycle** | Gerenciamento do ciclo de vida e transição dos documentos históricos |
| **S3 Glacier Deep Archive** | Retenção histórica de longo prazo para documentos com menor frequência de acesso |
| **S3 Object Lock** | Proteção dos objetos contra exclusão ou alteração durante o período de retenção configurado |
| **S3 Transfer Acceleration** | Otimização da transferência de arquivos entre clientes geograficamente distribuídos e o Amazon S3 |
| **AWS IAM** | Controle de permissões seguindo o princípio do menor privilégio |
| **Amazon CloudWatch** | Monitoramento, métricas, logs e acompanhamento operacional |
| **AWS CloudTrail** | Registro e auditoria das ações realizadas na conta e nos serviços AWS |
| **AWS CloudFormation** | Provisionamento e reprodução da infraestrutura por meio de código |

---

## Jornada do Cliente

A arquitetura técnica mostra como os serviços se conectam. Entretanto, para compreender a solução sob a perspectiva de quem utiliza a plataforma, também desenvolvemos uma visão focada na **Jornada do Cliente**.

Essa jornada representa o caminho percorrido pelo usuário desde o acesso à plataforma até a preservação histórica de seus documentos.

<p align="center">
  <img width="1536" height="1024" alt="Jornada do Cliente - Plataforma SaaS de Gestão de Documentos com IA" src="https://github.com/user-attachments/assets/205a90b4-dfd8-44de-83bf-c4a7f09828fc" />
</p>

A jornada foi organizada em três momentos principais:

### 1. Acesso e envio

O cliente acessa a plataforma, realiza sua autenticação e envia um documento para o processamento da aplicação. Nesse momento, o objetivo é proporcionar uma experiência simples ao usuário sem abrir mão da segurança e da identificação correta da propriedade do documento.

### 2. Proteção e utilização

Após o envio, o documento é associado à conta do cliente e armazenado de forma segura. Quando o usuário deseja consultar ou baixar um arquivo, a plataforma verifica sua identidade e suas permissões antes de liberar o acesso.

Dessa forma, o cliente não recebe acesso irrestrito ao ambiente de armazenamento. O acesso é concedido somente ao documento solicitado e de forma controlada.

### 3. Preservação histórica

Com o passar do tempo, os documentos continuam preservados como parte do histórico da empresa. Conforme seu padrão de acesso muda, a estratégia de armazenamento permite otimizar os custos sem perder o histórico que poderá gerar valor para o negócio no futuro.

Essa visão reforça um dos princípios centrais do projeto: **a segurança e a preservação dos dados devem estar presentes durante toda a jornada do cliente, e não apenas no momento do armazenamento**.

---

## Arquitetura AWS

A visão técnica da solução apresenta os serviços AWS utilizados e o fluxo principal de comunicação entre os componentes da arquitetura.

<p align="center">
  <img width="1536" height="1024" alt="Arquitetura AWS - Plataforma SaaS de Gestão de Documentos com IA" src="https://github.com/user-attachments/assets/a66c13f6-633b-4e12-8084-bc7727b39b90" />
</p>

O fluxo principal pode ser resumido da seguinte forma:

1. O usuário realiza o login na plataforma utilizando o **Amazon Cognito**.
2. Após a autenticação, o usuário recebe um token de identidade.
3. As solicitações são enviadas para o **Amazon API Gateway**, que atua como ponto de entrada da API.
4. O **AWS Lambda** processa a solicitação e aplica as regras de negócio.
5. Quando necessário, a função consulta os metadados no **Amazon DynamoDB** para validar a propriedade e a autorização relacionadas ao documento.
6. Após a validação, a aplicação gera uma URL pré-assinada para a operação solicitada no **Amazon S3**.
7. O usuário realiza o upload ou download diretamente no S3 utilizando essa autorização temporária.
8. Os documentos permanecem armazenados em um bucket privado e seguem a estratégia definida para seu ciclo de vida e retenção.

Além do fluxo principal, a arquitetura incorpora mecanismos de observabilidade, auditoria, controle de acesso, otimização de custos e infraestrutura como código.

É importante destacar que serviços como **S3 Lifecycle**, **S3 Intelligent-Tiering**, **S3 Glacier Deep Archive** e **S3 Object Lock** não representam etapas pelas quais uma requisição do usuário necessariamente passa em tempo real. Eles fazem parte da estratégia de gerenciamento e preservação dos dados ao longo de seu ciclo de vida.

---

## Arquitetura, AWS CAF e AWS Well-Architected Framework

A construção da solução também foi orientada por boas práticas de arquitetura em nuvem, considerando princípios presentes no **AWS Cloud Adoption Framework (AWS CAF)** e no **AWS Well-Architected Framework**.

O AWS CAF contribui para analisar a adoção da nuvem de forma mais ampla, considerando aspectos que vão além da tecnologia. No contexto deste projeto, ele ajuda a relacionar a arquitetura às necessidades do negócio, à segurança, à operação e à gestão dos recursos utilizados.

Já o AWS Well-Architected Framework oferece princípios técnicos para avaliar se uma arquitetura está sendo construída de maneira segura, confiável, eficiente e sustentável.

A relação da arquitetura com esses princípios pode ser observada da seguinte forma:

### 🔐 Segurança

O projeto prioriza a autenticação dos usuários, o controle de permissões e a validação da propriedade dos documentos antes da liberação do acesso.

O **Amazon Cognito**, o **AWS IAM**, o **Amazon API Gateway**, o **AWS Lambda** e o uso de URLs pré-assinadas contribuem para que o acesso aos dados seja controlado e limitado às operações autorizadas.

### 📈 Escalabilidade e performance

A utilização de serviços serverless permite que a solução acompanhe a demanda sem depender de uma única máquina responsável pelo processamento das solicitações.

O **Amazon API Gateway**, o **AWS Lambda**, o **Amazon DynamoDB** e o **Amazon S3** oferecem uma base gerenciada para o crescimento da aplicação.

O **S3 Transfer Acceleration** complementa essa estratégia ao otimizar a transferência de arquivos em cenários nos quais os clientes estão geograficamente distribuídos.

### 🛡️ Confiabilidade e preservação

O **Amazon S3** oferece uma base durável para o armazenamento dos documentos, enquanto a estratégia de ciclo de vida permite preservar o histórico ao longo do tempo.

O **S3 Object Lock** reforça a proteção dos objetos contra exclusão ou alteração durante o período de retenção configurado, contribuindo para o requisito de preservação histórica.

### 💰 Otimização de custos

A arquitetura reconhece que documentos recentes e históricos possuem padrões de acesso diferentes.

Por esse motivo, recursos como **S3 Intelligent-Tiering**, **S3 Lifecycle** e **S3 Glacier Deep Archive** fazem parte da estratégia para adequar o armazenamento ao comportamento dos dados e evitar que todo o histórico permaneça em uma camada voltada ao acesso frequente.

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

A arquitetura apresentada na Fase 01 foi desenvolvida para atender aos principais requisitos do cenário proposto, priorizando segurança, isolamento entre clientes, escalabilidade, retenção dos documentos, otimização de custos, observabilidade e reprodutibilidade da infraestrutura.

Como parte da evolução da solução, identificamos alguns pontos que podem ser aprimorados em uma segunda fase do projeto. Essas melhorias não são necessárias para que a arquitetura inicial atenda aos requisitos definidos, mas representam oportunidades para aumentar o nível de segurança e governança da plataforma conforme o negócio cresça e a quantidade e sensibilidade dos dados aumentem.

### 🔐 Fase 02 — Evolução da Segurança e Governança

A Fase 02 tem como principal objetivo fortalecer a proteção dos dados e o gerenciamento de informações sensíveis, complementando os mecanismos de segurança já presentes na Fase 01.

Os serviços avaliados para esta etapa são:

| Serviço | Objetivo na Fase 02 |
|---|---|
| **AWS KMS** | Gerenciamento centralizado de chaves criptográficas e maior controle sobre a proteção dos dados |
| **AWS Secrets Manager** | Armazenamento e gerenciamento seguro de credenciais, segredos e informações sensíveis utilizadas pela aplicação |
| **Amazon Macie** | Descoberta e identificação de dados sensíveis armazenados no Amazon S3, apoiando a classificação e a proteção das informações |

A adoção desses serviços deve ser avaliada considerando o crescimento da plataforma, o nível de sensibilidade dos documentos armazenados e o impacto financeiro de sua utilização.

A proposta não é adicionar serviços simplesmente para aumentar a quantidade de componentes da arquitetura. Cada recurso deve ser incorporado quando houver uma necessidade concreta que justifique seu uso, considerando segurança, governança, complexidade operacional e custo.

### 🚀 Como a solução pode evoluir?

A evolução da plataforma pode ser analisada a partir de algumas perguntas importantes:

- Como a solução poderia atender a um volume significativamente maior de usuários e documentos?
- Como aumentar o nível de proteção dos dados conforme a quantidade e a sensibilidade das informações cresçam?
- Como identificar e monitorar automaticamente a presença de informações sensíveis nos documentos armazenados?
- Como melhorar o gerenciamento de credenciais e informações confidenciais utilizadas pela aplicação?
- Como aumentar o controle sobre as chaves utilizadas para proteger os dados?
- Como manter o crescimento da plataforma sustentável sem aumentar os custos de forma desproporcional?

A Fase 02 representa, portanto, uma evolução natural da arquitetura, na qual mecanismos adicionais de segurança e governança podem ser incorporados conforme as necessidades do negócio se tornem mais complexas.

### 📈 Visão de futuro

Em um cenário de crescimento da Startup XYZ, a arquitetura poderá evoluir para atender a um volume maior de usuários, documentos e processamento, mantendo os princípios que orientaram a solução desde sua concepção.

Entre as possibilidades de evolução estão:

- **Maior proteção criptográfica:** utilização do AWS KMS para ampliar o controle sobre as chaves criptográficas e os mecanismos de proteção dos dados.
- **Gestão de informações sensíveis:** utilização do AWS Secrets Manager para centralizar e proteger credenciais e outros segredos utilizados pela aplicação.
- **Descoberta de dados sensíveis:** utilização do Amazon Macie para identificar e classificar informações potencialmente sensíveis armazenadas no Amazon S3.
- **Maior governança:** ampliação dos mecanismos de auditoria, monitoramento e controle conforme a plataforma cresça.
- **Escalabilidade:** evolução da arquitetura para suportar um aumento significativo no número de usuários e documentos sem depender de componentes individuais que limitem o crescimento.
- **Otimização de custos:** revisão contínua das estratégias de armazenamento e utilização dos serviços conforme o comportamento real da aplicação.

Essas melhorias não precisam necessariamente ser implementadas na primeira versão da solução. O objetivo desta etapa é demonstrar que a arquitetura foi pensada não apenas para atender ao cenário atual, mas também para permitir uma evolução consistente conforme o negócio cresça.

> **A Fase 01 resolve o problema atual. A Fase 02 prepara a arquitetura para os desafios que surgem com o crescimento da plataforma.**

---

# 6. Como o projeto foi desenvolvido

> 🚧 **Em desenvolvimento**
>
> Nesta seção será apresentada a forma como o projeto foi organizado e desenvolvido pela equipe, incluindo as principais etapas de análise, definição de requisitos, tomada de decisões técnicas e construção da proposta de solução.

---

# 7. Infraestrutura como Código

A infraestrutura da solução foi planejada para ser reproduzível e consistente entre diferentes ambientes. A utilização de **Infrastructure as Code (IaC)** permite transformar a arquitetura definida no projeto em recursos provisionados por meio de código.

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

Configurações de bloqueio de acesso público e como a configuração sobrepõe políticas que liberariam acesso público.

https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-block-public-access.html

### 2. Amazon S3 — URLs pré-assinadas

Como gerar URLs temporárias que concedem acesso restrito a um único objeto, sem tornar o bucket público.

https://docs.aws.amazon.com/AmazonS3/latest/userguide/ShareObjectPreSignedURL.html

### 3. AWS re:Post (Knowledge Center oficial da AWS) — Acesso por prefixo

Exemplo oficial de política de IAM que usa a condição s3:prefix com variável de identidade para restringir cada usuário ao seu próprio prefixo dentro de um bucket compartilhado.

https://repost.aws/knowledge-center/s3-folder-user-access

### 4. Amazon S3 — Gerenciamento do ciclo de vida de objetos

Como as regras de S3 Lifecycle transicionam objetos para classes de menor custo, com exemplos de uso para dados de retenção regulatória e histórica.

https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html

### 5. Amazon API Gateway — Features

Papel do API Gateway como camada de publicação, segurança, monitoramento e limitação de tráfego (throttling) de APIs, incluindo integração direta com AWS Lambda.

https://aws.amazon.com/api-gateway/features/

### 6. AWS Lambda (página de produto)

Modelo de execução orientado a evento, exemplo oficial de acionamento por upload no S3, e cobrança por uso sem custo de infraestrutura ociosa.

https://aws.amazon.com/lambda/lambda-functions/

### 7. G1 Tecnologia — reportagem jornalística

Caso da Polícia de Xangai (2022): alegação de exposição de registros associados a cerca de 1 bilhão de cidadãos por falha de configuração em nuvem — usado no Ato 1 como gancho de dor, não como fonte técnica AWS.

https://g1.globo.com/tecnologia/noticia/2022/07/04/hacker-alega-ter-roubado-da-policia-registros-de-1-bilhao-de-chineses.ghtml

### 8. IBM — Relatório do Custo das Violações de Dados

Estudo anual da IBM sobre custo e causas de violações de dados, usado no Ato 1 para sustentar que falhas de configuração são um problema recorrente, não um caso isolado.

**Relatório do Custo das Violações de Dados 2026: O Ponto de Virada da IA (2026) — IBM.**
