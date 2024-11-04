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
