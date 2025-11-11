
# AWS para Ciência de Dados ☁️ ☁️

Repositório de apoio ao curso **AWS para Ciência de Dados** desenvolvido para a Alura.

---

## Sobre o Curso

Este curso introduz de forma prática o uso da Amazon Web Services (AWS) no contexto da Ciência de Dados.
Ao longo das aulas, você aprenderá a utilizar os principais serviços da AWS para construir um pipeline completo de dados — desde o armazenamento de informações no Amazon S3, passando pela catalogação e transformação com o AWS Glue, até a análise com o Athena e o treinamento de modelos no SageMaker.



## Conteúdo

### Aula 1: IAM, Custos e Boas Práticas

- Sobre os créditos da AWS:  
  [What are AWS Credits?](https://www.nops.io/glossary/what-are-aws-credits/)
- Sobre a camada gratuita:
  [Nível gratuito da AWS](https://aws.amazon.com/pt/free/)


<details>
<summary>Exemplo prático criando uma política</summary>

Tarefa: Você precisa criar um usuário para uma outra pessoa, essa pessoa ela deve ter acesso para baixar, deletar e dar upload em objetos no bucket, apenas em seu bucket chamado "meubucketpessoal".

Para começar, você deve criar a política. A política é o que define as permissões do usuário. Vamos criar uma que permite ler, gravar e deletar arquivos apenas no seu bucket.

1. No painel do IAM, clique em **"Policies"** (Políticas) no menu lateral esquerdo. 
2. Clique no botão **"Create policy"** (Criar política).
3. Você verá um editor de políticas. Selecione a aba "JSON".
4. E cole o seguinte código:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:DeleteObject"
            ],
            "Resource": "arn:aws:s3:::meubucketpessoalt/*"
        },
        {
            "Sid": "VisualEditor1",
            "Effect": "Allow",
            "Action": "s3:ListBucket",
            "Resource": "arn:aws:s3:::meubucketpessoal"
        }
    ]
}
```

**Action:**

Lista as **ações específicas** que o usuário pode executar.

Nesse caso:

- `"s3:PutObject"` → permite **enviar (fazer upload)** de arquivos para o bucket.
- `"s3:GetObject"` → permite **baixar ou ler** arquivos do bucket.
- `"s3:ListBucket"` → permite **listar** os objetos dentro do bucket.
- `"s3:DeleteObject"` → permite **excluir** arquivos.
- `"s3:PutObjectAcl"` → permite **definir permissões de acesso (ACL)** nos objetos.

**Resource:**

Define **onde** essas ações são válidas:

- `"arn:aws:s3:::<bucket name>"` → se refere **ao bucket em si**.
- `"arn:aws:s3:::<bucket name>/*"` → se refere **a todos os objetos dentro desse bucket**.

5. Clique em **"Next: Tags"** e depois em **"Next: Review"**.
6. Dê um nome para sua política (por exemplo, S3-meu-bucket-RW-Policy) e adicione uma descrição.
7. Clique em **"Create policy"**.

</details>
  

### Aula 2: Armazenamento na AWS

- **Base de dados:** [Heart Failure Prediction Dataset](https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction)  
  > Este conjunto de dados foi criado ao combinar cinco bases independentes sobre doenças cardíacas — Cleveland, Hungarian, Switzerland, Long Beach VA e Stalog — unificadas a partir de 11 variáveis em comum. O resultado é o maior dataset consolidado já disponível para pesquisa na área, totalizando 918 registros de pacientes.



### Aula 3 e 4: Analisando os dados e criando modelos em instâncias de notebook no Sagemaker

- Notebook: [`Heart_model.ipynb`]()
- [One Hot Encoding Python Tutorial](https://www.datacamp.com/tutorial/one-hot-encoding-python-tutorial) - DataCamp



### Aula 5: ETL com AWS Glue

- [AWS Glue Data Catalog Best Practices](https://docs.aws.amazon.com/glue/latest/dg/best-practice-catalog.html)


### Aula 6: Consultando dados com Athena


## Bases de dados e ideias para projetos futuros

- [Datasets Kaggle](https://www.kaggle.com/datasets)
- [Portal Brasileiro de Dados Abertos](https://dados.gov.br/home)
- [UCI Repositório de Machine Learning](https://archive.ics.uci.edu/)
- [Dados abertos do governo americano](https://data.gov/)
- [Sidra IBGE](https://sidra.ibge.gov.br/home/ipca15/brasil)
- [Dados sobre câncer](https://www.cancerimagingarchive.net/access-data/): O TCIA (“Acervo de Imagens de Câncer”) é um repositório público mantido pela National Cancer Institute (NCI) dos EUA, dedicado a armazenar e disponibilizar para download imagens médicas relacionadas ao câncer e também dados estruturados.



## Estrutura do Repositório

```
📓 Heart_Disease.ipynb
📁 dados/
    ├── heart.csv
    ├── heart_model.ipynb
    
```














