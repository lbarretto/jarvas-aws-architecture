# ☁️ Startup Jarva's - Plataforma SaaS de Gestão de Documentos com IA

<!-- CAPA DO PROJETO -->
<p align="center">
  <img src="./assets/cover.png" alt="Capa do projeto Startup XYZ">
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
- [5. Da necessidade à solução](#5-da-necessidade-à-solução)
- [6. Referências](#6-referências)

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

# 5. Da necessidade à solução

A partir desses requisitos, fica claro que o desafio da Startup XYZ não está apenas em armazenar uma grande quantidade de documentos. A arquitetura precisa acompanhar o crescimento da empresa, proteger os dados de cada cliente, preservar o histórico como um ativo estratégico e, ao mesmo tempo, manter os custos sob controle.

É a partir dessas necessidades que chegamos à proposta de arquitetura deste projeto. A escolha dos serviços AWS não parte, portanto, da tecnologia em si, mas dos problemas que precisam ser resolvidos e dos requisitos que a solução precisa atender.

**Nas próximas etapas, apresentamos como esses requisitos foram traduzidos em uma arquitetura AWS, quais serviços foram selecionados e quais decisões técnicas orientaram a construção da solução.**

---

# 6. Referências

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
