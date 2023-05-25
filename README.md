# mlops-mlflow-deployment

### Build Docker Image

```sh
# Mac computers with Apple silicon requires --platform linux/amd64
docker build -t mlflow-postgres-with-s3:latest . --platform linux/amd64
# or
docker build -t mlflow-postgres-with-s3:latest .
```

### Run The Docker

```sh
lsof -i -P -n | grep 5050
kill -9 $(lsof -t -i tcp:5050)
docker run -it -p 5050:5050 --env-file docker.env mlflow-postgres-with-s3:latest --platform linux/amd64
```

### Push ECR

```
aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin 932682266260.dkr.ecr.ap-southeast-1.amazonaws.com
```
