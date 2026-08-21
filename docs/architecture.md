# Arquitetura AWS — Jarvas

![Arquitetura AWS da plataforma Jarvas](../assets/aws-architecture.svg)

## Visão geral

A solução usa serviços gerenciados e serverless para armazenar documentos de forma segura, escalável e isolada por usuário. O cliente nunca recebe credenciais da AWS: todas as operações são autorizadas pelo backend e o tráfego de arquivos ocorre por URLs pré-assinadas de curta duração.

## Fluxos principais

### Autenticação e autorização

1. O usuário autentica no Amazon Cognito e recebe um token JWT.
2. O cliente chama o Amazon API Gateway usando o token.
3. O autorizador do Cognito valida o token antes da invocação das funções Lambda.
4. A função extrai o identificador imutável do usuário (`sub`) do token e o usa como chave de isolamento. O cliente não pode escolher outro proprietário.

### Upload

1. A API valida tipo, tamanho e nome lógico do arquivo.
2. Uma função Lambda cria uma URL pré-assinada de curta duração para uma chave no formato `users/{sub}/documents/{documentId}`.
3. O cliente envia o conteúdo diretamente ao Amazon S3 usando HTTPS.
4. A aplicação grava no DynamoDB somente os metadados do documento e seu estado.
5. O versionamento do bucket preserva o histórico das alterações.

### Download

1. O cliente solicita acesso ao documento pela API autenticada.
2. A função consulta o DynamoDB e confirma que o proprietário é o mesmo `sub` autenticado.
3. Somente após essa validação é gerada uma URL pré-assinada de download, com expiração curta.
4. O cliente baixa o objeto diretamente do S3 por HTTPS.

## Controles de segurança

- Bloqueio total de acesso público no bucket e política que exige TLS.
- Criptografia em repouso no S3 e no DynamoDB com AWS KMS.
- Criptografia em trânsito com HTTPS/TLS.
- IAM por função, com ações e recursos mínimos necessários.
- Chaves do S3 particionadas por `sub` e autorização conferida no backend.
- URLs pré-assinadas com validade curta; nenhum objeto é público.
- Versionamento do S3 para preservação histórica e recuperação.
- Logs, métricas e alarmes no CloudWatch, sem registrar tokens nem URLs assinadas.

## Modelo sugerido no DynamoDB

| Campo | Uso |
| --- | --- |
| `PK = USER#{sub}` | Partição e isolamento do proprietário |
| `SK = DOC#{documentId}` | Identificação do documento |
| `s3Key` | Referência para o objeto no S3 |
| `fileName`, `contentType`, `size` | Metadados funcionais |
| `status`, `createdAt`, `updatedAt` | Estado e auditoria básica |

## Infraestrutura e operação

Todos os recursos devem ser definidos em templates do AWS CloudFormation e separados por ambiente. CloudWatch centraliza logs, métricas e alarmes de erros, latência e throttling. Políticas de ciclo de vida do S3 podem migrar versões antigas para classes mais econômicas e expirar uploads incompletos.

> O diagrama representa a arquitetura-alvo. Os templates CloudFormation e o código das funções devem ser adicionados em contribuições posteriores, acompanhados de testes automatizados e estimativa de custos.
