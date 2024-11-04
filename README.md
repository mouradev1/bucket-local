## Bucket local


## Configuração do ambiente
* No arquivo init-s3.py definir suas keys local
```python
import boto3

s3_client = boto3.client(
    "s3",
    endpoint_url=f"http://localhost:4566",
    aws_access_key_id="test",
    aws_secret_access_key="test"
)

s3_client.create_bucket(Bucket="your-bucket")

```

## Subir o ambiente
```bash
docker-compose up -d
```

## Configurando na aplicação laravel
* No arquivo .env adicionar as seguintes variáveis
```env
AWS_ACCESS_KEY_ID=test
AWS_SECRET_ACCESS_KEY=test
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=your-bucket
AWS_URL=http://localhost:4566
AWS_ENDPOINT=http://localhost:4566

```

## Realizando testes com o s3 local
```bash
export AWS_ACCESS_KEY_ID="test"
export AWS_SECRET_ACCESS_KEY="test"
export AWS_DEFAULT_REGION="us-east-1"

aws --endpoint-url=http://localhost:4566 s3api list-buckets

```
## Possiveis erros  

```log
Traceback (most recent call last):
  File "/usr/bin/aws", line 19, in <module>
    import awscli.clidriver
  File "/usr/lib/python3/dist-packages/awscli/clidriver.py", line 17, in <module>
    import botocore.session
  File "/usr/lib/python3/dist-packages/botocore/session.py", line 29, in <module>
    import botocore.credentials
```
## Solução

```bash
pip install 'urllib3<2.0'

```