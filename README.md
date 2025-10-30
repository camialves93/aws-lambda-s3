# aws-lambda-s3
Tarefas automatizadas com Lambda Function e S3

Este repositório tem como objetivo centralizar anotações, códigos de exemplo e boas práticas para o aprendizado de tarefas automatizadas na AWS, com foco em Lambda Functions e eventos do Amazon S3.

## Fluxo do Processo

Usuário faz upload de um arquivo .json no Amazon S3.

O S3 gera um evento que aciona automaticamente a AWS Lambda.

A Lambda lê, valida e grava os dados no Amazon DynamoDB.

| Serviço AWS                | Função                                            |
| -------------------------- | ------------------------------------------------- |
| **Amazon S3**              | Armazenamento dos arquivos                        |
| **AWS Lambda**             | Processamento automático dos dados                |
| **Amazon DynamoDB**        | Banco de dados NoSQL para armazenamento das notas |
| **IAM**                    | Controle de acesso e permissões                   |
| **API Gateway (opcional)** | Exposição dos dados via API RESTful               |

## S3 para Lambda 

{
  "Records": [
    {
      "s3": {
        "bucket": { "name": "notas-fiscais-json" },
        "object": { "key": "nota_2025-10-29.json" }
      }
    }
  ]
}


### Etapas internas da Lambda 
Extrair nome do bucket e arquivo.

Ler o JSON do S3.

Validar estrutura e campos obrigatórios.

Salvar no DynamoDB.

Registrar logs no CloudWatch.

### Aprendizados chave de notas 
Serverless = Menos infraestrutura para gerenciar.

Eventos do S3 são ideais para automações reativas (upload → ação automática).

Funções pequenas e bem definidas são mais fáceis de manter.

Permissões IAM precisam ser configuradas com o princípio do menor privilégio.

CloudWatch Logs é essencial para debugar execuções Lambda.


