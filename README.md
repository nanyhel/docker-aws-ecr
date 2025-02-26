# Docker AWS ECR Project

Este proyecto proporciona una guía para configurar y desplegar contenedores Docker en Amazon Elastic Container Registry (ECR).

## Requisitos

- Docker
- AWS CLI
- Cuenta de AWS

## Configuración

1. **Instalar Docker**: [Guía de instalación de Docker](https://docs.docker.com/get-docker/)
2. **Instalar AWS CLI**: [Guía de instalación de AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
3. **Configurar AWS CLI**:
    ```sh
    aws configure
    ```

## Uso

1. **Construir la imagen Docker**:
    ```sh
    docker build -t nombre-imagen .
    ```

2. **Crear un repositorio en ECR**:
    ```sh
    aws ecr create-repository --repository-name nombre-repositorio
    ```

3. **Iniciar sesión en ECR**:
    ```sh
    aws ecr get-login-password | docker login --username AWS --password-stdin <aws_account_id>.dkr.ecr.<region>.amazonaws.com
    ```

4. **Etiquetar la imagen**:
    ```sh
    docker tag nombre-imagen:latest <aws_account_id>.dkr.ecr.<region>.amazonaws.com/nombre-repositorio:latest
    ```

5. **Subir la imagen a ECR**:
    ```sh
    docker push <aws_account_id>.dkr.ecr.<region>.amazonaws.com/nombre-repositorio:latest
    ```