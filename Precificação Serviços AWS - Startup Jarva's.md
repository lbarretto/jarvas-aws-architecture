# 💰 Precificação da Arquitetura AWS —  Startup Jarva's - Plataforma SaaS de Gestão de Documentos com IA

<!-- CAPA DA PRECIFICAÇÃO -->
<p align="center">
  <em></em>
</p>

> **Justificativa técnica e financeira da arquitetura AWS da Fase 01 — Plataforma SaaS de Gestão de Documentos com IA — com base em uma estimativa oficial da AWS Pricing Calculator.**

---

<details open>
<summary><h2>📌 Sumário</h2></summary>

### 1️⃣ [Visão geral dos custos](#1-visão-geral-dos-custos)

### 2️⃣ [O problema de negócio por trás da precificação](#2-o-problema-de-negócio-por-trás-da-precificação)
- [O ciclo de vida dos documentos](#o-ciclo-de-vida-dos-documentos)
- [A curva de leitura](#a-curva-de-leitura)

### 3️⃣ [Como chegamos a 410.000 leituras por mês](#3-como-chegamos-a-410000-leituras-por-mês)

### 4️⃣ [Custo por serviço](#4-custo-por-serviço)
- [Amazon S3 Intelligent-Tiering](#amazon-s3-intelligent-tiering)
- [Amazon S3 Glacier Deep Archive](#amazon-s3-glacier-deep-archive)
- [Transferência de dados (Data Transfer)](#transferência-de-dados-data-transfer)
- [Amazon API Gateway](#amazon-api-gateway)
- [AWS Lambda](#aws-lambda)
- [Amazon DynamoDB](#amazon-dynamodb)
- [Amazon Cognito](#amazon-cognito)
- [S3 Transfer Acceleration (opcional)](#s3-transfer-acceleration-opcional)
- [AWS IAM](#aws-iam)
- [Amazon CloudWatch](#amazon-cloudwatch)
- [AWS CloudTrail](#aws-cloudtrail)
- [AWS CloudFormation](#aws-cloudformation)
- [Amazon S3 Object Lock](#amazon-s3-object-lock)

### 5️⃣ [Resumo consolidado de custos](#5-resumo-consolidado-de-custos)

### 6️⃣ [Custo inicial explicado](#6-custo-inicial-explicado)

### 7️⃣ [Onde há gratuidade, e até quando ela dura](#7-onde-há-gratuidade-e-até-quando-ela-dura)

### 8️⃣ [Referências e estimativa oficial](#8-referências-e-estimativa-oficial)

</details>

---

# 1. Visão geral dos custos

A tabela abaixo resume os quatro números que resumem a saúde financeira da arquitetura da Fase 01:

| | |
|---|---|
| 💵 **US$ 143,54 / mês** | Custo mensal recorrente da arquitetura |
| 🧾 **US$ 33,00** | Custo inicial — pagamento único na criação dos recursos |
| 📅 **US$ 1.755,48** | Projetado em 12 meses *(já inclui o custo inicial de US$ 33,00)* |
| 📄 **US$ 0,0029** | Custo por documento processado / mês |

> **O custo mensal recorrente representa menos de US$ 0,003 por documento processado — um indicador direto de que a arquitetura escala com custo marginal muito baixo por unidade de valor entregue.**

---

# 2. O problema de negócio por trás da precificação

A Startup Jarva's opera um agente de inteligência artificial que extrai dados de documentos enviados por seus clientes — cerca de **50.000 arquivos novos todo mês**, com tamanho médio de **10 MB** cada.

O desafio de negócio tem duas exigências que competem entre si:

- os clientes precisam acessar seus documentos normalmente durante o primeiro ano;
- nenhum arquivo pode ser excluído depois disso, pois o histórico acumulado é o ativo que alimentará o treinamento de futuros modelos de IA.

Essas duas exigências são o que justifica toda a arquitetura de custos descrita neste documento.

## O ciclo de vida dos documentos

A solução se apoia em uma ideia simples: **nem todo documento precisa do mesmo nível de disponibilidade para sempre**. A arquitetura reflete esse ciclo de vida, movendo cada documento por três estágios de custo decrescente:

| Estágio | Período | Onde o arquivo fica | Nível de acesso esperado |
|---|---|---|---|
| 🔥 Quente | Meses 1 a 3 | S3 Intelligent-Tiering | Alto — consultas frequentes do cliente e da IA |
| 🌤️ Morno | Meses 4 a 6 | S3 Intelligent-Tiering | Baixo — consultas ocasionais |
| ❄️ Frio | Meses 7 a 12 | S3 Intelligent-Tiering | Muito baixo — praticamente histórico |
| 🗄️ Arquivo permanente | A partir do mês 13 | S3 Glacier Deep Archive | Nulo — retido como ativo de dados |

## A curva de leitura

Para transformar esse ciclo de vida em um número de custo, foi necessário estimar quantas vezes, em média, um cliente volta a abrir um documento depois de enviá-lo — e como essa frequência cai com o tempo:

| Idade do documento | Leituras/mês estimadas |
|---|---|
| 1º mês (mais recente) | 3 |
| 2º mês | 2 |
| 3º mês | 1 |
| 4º ao 6º mês | 0,3 cada |
| 7º ao 12º mês | 0,05 cada |

> **Esclarecimento importante:** na operação real, o Amazon S3 Intelligent-Tiering decide sozinho e automaticamente em qual nível cada arquivo permanece, observando o acesso de fato. A curva de leitura não é uma regra imposta ao serviço — é a melhor estimativa desse comportamento, necessária porque a calculadora de custos não tem acesso a dados reais de uso ainda, já que o produto está em fase de lançamento.

---

# 3. Como chegamos a 410.000 leituras por mês

Esse número é a soma de duas origens de leitura diferentes, medidas em um mês típico de operação já madura — quando a plataforma já acumulou 12 meses de arquivos coexistindo simultaneamente, cada um em um estágio diferente do seu ciclo de vida.

- **Leitura pela própria IA (processamento):** todo documento novo é lido uma vez pelo sistema no mês em que chega → **50.000 leituras fixas/mês**.
- **Leitura pelo cliente:** aqui é onde a curva de leitura entra em ação, somando a contribuição de 12 grupos de arquivos de idades diferentes.

| Idade do grupo | Leituras/doc. no mês | Documentos no grupo | Leituras geradas |
|---|---|---|---|
| 1 mês (mais recente) | 3 | 50.000 | 150.000 |
| 2 meses | 2 | 50.000 | 100.000 |
| 3 meses | 1 | 50.000 | 50.000 |
| 4, 5 e 6 meses | 0,3 cada | 50.000 cada | 45.000 |
| 7 a 12 meses | 0,05 cada | 50.000 cada | 15.000 |
| **Subtotal — leitura de cliente** | | | **360.000** |
| Leitura de sistema (IA) | | | 50.000 |
| **Total de leituras por mês** | | | **410.000** |

> Não faria sentido multiplicar simplesmente 50.000 documentos por um número fixo de leituras, porque em qualquer mês existem arquivos "novos" e "antigos" sendo lidos ao mesmo tempo, cada um com uma frequência diferente. Somar a contribuição de cada grupo, respeitando sua idade, é o que torna essa estimativa realista.

---

# 4. Custo por serviço

## Amazon S3 Intelligent-Tiering

Camada responsável por manter os documentos acessíveis durante o primeiro ano de vida de cada arquivo.

| Parâmetro | Valor |
|---|---|
| Armazenamento mensal | 5.859 GB |
| Tamanho médio do objeto | 10 MB |
| Uploads (PUT) por mês | 50.000 |
| Leituras (GET) por mês | 410.000 |
| Distribuição entre níveis | 25% quente / 25% morno / 50% frio |

**Custo mensal:** US$ 65,63 *(46% do custo total da arquitetura)* + **US$ 3,00 de custo inicial** (pagamento adiantado).

O Intelligent-Tiering foi escolhido em vez de uma classe fixa porque move os arquivos automaticamente entre níveis de custo conforme o uso real diminui — sem regra manual de transição e sem taxa de recuperação.

## Amazon S3 Glacier Deep Archive

Destino final de cada documento, para onde é movido automaticamente pela regra de ciclo de vida (Lifecycle) assim que completa 365 dias na camada quente.

| Parâmetro | Valor |
|---|---|
| Armazenamento | 5.859 GB *(fotografia do mês 24)* |
| Transições por mês | 50.000 |
| Restaurações simuladas | Nenhuma |

**Custo mensal:** US$ 8,42 *(6% do custo total)* + **US$ 30,00 de custo inicial** — a maior parte do custo inicial total da arquitetura.

É a classe de armazenamento de menor custo por gigabyte da AWS, adequada porque o requisito de negócio é reter dados sem necessidade de acesso imediato.

## Transferência de dados (Data Transfer)

Cobre o tráfego gerado quando um cliente baixa ou visualiza um documento próprio via URL pré-assinada.

| Direção | Volume mensal | Justificativa |
|---|---|---|
| Entrada (upload) | Sem custo | Upload direto cliente → S3; a AWS não cobra entrada |
| Saída (download) | ≈ 3,4 TB | 360.000 leituras de cliente × 10 MB por arquivo |

**Custo mensal:** US$ 61,44 *(43% do custo total da arquitetura)* — consequência direta e inevitável de entregar aos clientes o acesso aos próprios documentos.

## Amazon API Gateway

Ponto único pelo qual toda solicitação do cliente (upload ou download) chega à aplicação.

| Parâmetro | Valor |
|---|---|
| Tipo de API | REST |
| Solicitações por mês | 500.000 |
| Cache dedicado | Não utilizado |

**Custo mensal:** US$ 0,50 *(< 1% do custo total)*

## AWS Lambda

Função que valida a identidade do usuário, verifica a propriedade do documento e gera a URL pré-assinada.

| Parâmetro | Valor |
|---|---|
| Solicitações por mês | 500.000 |
| Duração média | 200 ms |
| Memória alocada | 128 MB |

**Custo mensal:** US$ 0,00 — o consumo estimado fica bem abaixo do nível gratuito permanente (1M solicitações + 400.000 GB-s/mês).

## Amazon DynamoDB

Banco de metadados dos documentos, consultado a cada operação para validar a propriedade antes de qualquer acesso ao S3.

| Parâmetro | Valor |
|---|---|
| Modelo de capacidade | Sob demanda |
| Armazenamento | 1,14 GB |
| Gravações por mês | 50.000 |
| Leituras por mês | 500.000 |
| Consistência de leitura | 100% forte |

**Custo mensal:** US$ 0,37 *(< 1% do custo total)*

## Amazon Cognito

Login dos clientes, emissão de tokens e MFA opcional.

| Parâmetro | Valor |
|---|---|
| Nível de serviço | Cognito Essentials |
| Usuários ativos/mês (MAU) | 5.000 |
| Federação externa | Não utilizada |

**Custo mensal:** US$ 0,00 — a base de usuários opera em metade da cota gratuita (10.000 MAU/mês).

## S3 Transfer Acceleration (opcional)

Recurso **opcional** que acelera a transferência entre clientes geograficamente distantes e o bucket S3 — soma-se ao custo já calculado, não o substitui, por isso fica fora do total-base.

| Direção | Volume mensal | Tarifa oficial AWS | Custo mensal |
|---|---|---|---|
| Entrada (upload) | 488 GB | US$ 0,08/GB — fora de EUA, Europa e Japão | US$ 39,06 |
| Saída (download) | 3.516 GB | US$ 0,04/GB — tarifa única | US$ 140,62 |
| **Total do recurso** | | | **US$ 179,69** |

> **Recomendação:** este é o único componente da arquitetura com espaço claro para otimização de custo sem perda de funcionalidade — avaliar se todo o tráfego precisa da aceleração pode reduzir esse valor.

## AWS IAM

Controle de permissões entre os serviços, seguindo o princípio do menor privilégio.

**Custo mensal:** US$ 0,00 — um dos poucos serviços da AWS com gratuidade permanente e irrestrita.

## Amazon CloudWatch

Coleta os logs da função Lambda e mantém alarmes que sinalizam comportamentos fora do esperado.

| Parâmetro | Valor |
|---|---|
| Invocações monitoradas por mês | 500.000 |
| Volume de log ingerido por mês | ≈ 0,24 GB |
| Retenção configurada | 30 dias |
| Alarmes configurados | 5 |
| Painéis (dashboards) configurados | 5 |

**Custo mensal:** US$ 6,18 *(4% do custo total)*

O volume de logs fica dentro do nível gratuito permanente (5 GB de ingestão + 10 alarmes/mês). O custo vem dos **5 painéis configurados**: a AWS libera 3 gratuitos por conta, e os 2 adicionais são cobrados à parte.

## AWS CloudTrail

Registra quem fez o quê, quando e a partir de onde em toda a conta AWS.

| Parâmetro | Valor |
|---|---|
| Eventos de gerenciamento por mês | ≈ 10.000 *(gratuitos)* |
| Eventos de dados — operações no S3 | 460.000/mês |
| Eventos de dados — invocações do Lambda | 500.000/mês |
| CloudTrail Insights | Habilitado, 1 trilha |

**Custo mensal:** US$ 0,99 *(estimativa)* — ≈ US$ 0,96 de eventos de dados + ≈ US$ 0,04 de CloudTrail Insights.

## AWS CloudFormation

Define, versiona e provisiona todos os recursos da arquitetura a partir de um template único.

**Custo mensal:** US$ 0,00 — toda a stack usa exclusivamente serviços nativos da AWS, dentro do nível gratuito do serviço.

## Amazon S3 Object Lock

Impede tecnicamente a exclusão ou sobrescrita dos documentos durante o período de retenção — a garantia concreta por trás da regra "nenhum arquivo pode ser excluído".

| Parâmetro | Valor |
|---|---|
| Modo de retenção | Compliance |
| Pré-requisito técnico | S3 Versioning habilitado |
| Impacto em armazenamento | Nenhum adicional relevante |

**Custo mensal:** US$ 0,00 — a ativação em si não tem custo próprio.

---

# 5. Resumo consolidado de custos

| Serviço | Mensal (US$) | 12 meses (US$) | % do total-base |
|---|---|---|---|
| S3 Intelligent-Tiering | 65,63 | 790,56 | 46% |
| Transferência de dados (saída) | 61,44 | 737,28 | 43% |
| S3 Glacier Deep Archive | 8,42 | 131,04 | 6% |
| Amazon CloudWatch | 6,18 | 74,17 | 4% |
| Amazon API Gateway | 0,50 | 6,00 | < 1% |
| DynamoDB (sob demanda) | 0,37 | 4,44 | < 1% |
| AWS CloudTrail | 0,99 | 11,94 | < 1% |
| AWS Lambda | 0,00 | 0,00 | 0% |
| AWS IAM | 0,00 | 0,00 | 0% |
| AWS CloudFormation | 0,00 | 0,00 | 0% |
| Amazon S3 Object Lock | 0,00 | 0,00 | 0% |
| Amazon Cognito | 0,00 | 0,00 | 0% |
| **Total-base (estimativa oficial)** | **143,54** | **1.755,48** | **100%** |
| S3 Transfer Acceleration *(opcional)* | 179,69 | 2.156,28 | — |
| **Total com aceleração habilitada** | **323,23** | **3.911,76** | — |

> Dividindo o custo-base pelo volume mensal de documentos processados (US$ 143,54 ÷ 50.000), chega-se a aproximadamente **US$ 0,0029 por documento ao mês** — argumento central para a defesa da viabilidade financeira do case.

---

# 6. Custo inicial explicado

Além do custo mensal recorrente, a arquitetura tem um **custo inicial (pagamento adiantado) de US$ 33,00**, cobrado uma única vez na criação dos recursos:

| Origem | Custo inicial |
|---|---|
| S3 Intelligent-Tiering | US$ 3,00 |
| S3 Glacier Deep Archive | US$ 30,00 |
| **Total** | **US$ 33,00** |

Esse valor **não se repete todo mês** — ele está incluído apenas uma vez no total projetado em 12 meses:

```
US$ 143,54 × 12 = US$ 1.722,48
+ US$ 33,00 (custo inicial, pago uma única vez)
= US$ 1.755,48 projetado em 12 meses
```

A partir do segundo ano, sem novos pagamentos adiantados, o projetado anual cai para os **US$ 1.722,48** recorrentes.

---

# 7. Onde há gratuidade, e até quando ela dura

É importante distinguir dois tipos de gratuidade: **nível gratuito permanente**, que se renova todo mês sem prazo de validade, e **nível gratuito limitado aos primeiros 12 meses de conta**, que expira independentemente do volume de uso.

| Serviço | O que é gratuito | Duração | Custo após esgotar |
|---|---|---|---|
| AWS Lambda | 1M solicitações + 400.000 GB-s/mês | Permanente | Tarifa por 1M adicional + valor por GB-s |
| Amazon Cognito | 10.000 MAU/mês | Permanente | Tarifa por MAU excedente, por faixa |
| Data Transfer (saída) | 100 GB/mês, toda a conta | Permanente, mas consumido rápido | US$ 0,09/GB nos primeiros 10 TB |
| API Gateway (REST) | 1M chamadas/mês | Só nos primeiros 12 meses da conta | Cobrado desde a 1ª chamada, ano 2+ |
| DynamoDB (sob demanda) | Nenhuma | Não se aplica | Cobrado desde o 1º uso |
| S3 INT / Glacier Deep Archive | Nenhuma relevante | Não se aplica | Cobrado desde o 1º GB armazenado |
| S3 Transfer Acceleration | Nenhuma | Não se aplica | Cobrado desde o 1º GB transferido |
| AWS IAM | Gratuidade total e irrestrita | Permanente, sem limite | Não há cobrança em nenhuma circunstância |
| Amazon CloudWatch | 5 GB de logs + 10 alarmes/mês + 3 painéis | Permanente | Tarifa por GB de log, alarme ou painel excedente |
| AWS CloudTrail | 1ª trilha de eventos de gerenciamento | Permanente | Eventos de dados e Insights cobrados desde o 1º evento |
| AWS CloudFormation | 1.000 operações de extensão de terceiros/mês | Permanente | Não se aplica — projeto usa só tipos nativos |
| Amazon S3 Object Lock | Nenhuma tarifa própria | Não se aplica | Custo indireto só em caso de acúmulo de versões |

> **Leitura estratégica:** Lambda e Cognito permanecem gratuitos de forma permanente na escala atual, confirmando que o custo real do negócio está concentrado em armazenamento e transferência de dados, não em capacidade computacional. O Amazon CloudWatch é a única exceção parcial — seus 5 painéis de monitoramento ultrapassam o nível gratuito de 3, gerando US$ 6,18/mês (4% do total). O único item com prazo de expiração (API Gateway, limitado ao 1º ano da conta) representa menos de 1% do custo total, portanto sua expiração tem baixo impacto financeiro.

---

# 8. Referências e estimativa oficial

Estimativa elaborada com base na **AWS Pricing Calculator**, região **Leste dos EUA (N. da Virgínia)**. Os valores refletem premissas de negócio e projeções de uso; custos reais podem variar conforme o comportamento efetivo dos usuários e eventuais mudanças na tabela de preços da AWS.

🔗 [Acesse a estimativa completa na AWS Pricing Calculator](https://calculator.aws/#/estimate?id=10e31047407390d476f3571191e4dd586caeeda5)

---

<p align="center">
  <strong>☁️  Startup Jarva's</strong><br>
  Plataforma SaaS de Gestão de Documentos com IA — Precificação da Arquitetura AWS
</p>
