# conversao-distancia

# Projeto Python com Docker

Este projeto é uma aplicação Python que utiliza Gunicorn para servir o aplicativo. O ambiente é configurado usando Docker para facilitar a implantação e gerenciamento das dependências.

## Pré-requisitos

Antes de começar, certifique-se de ter instalado em sua máquina:

- [Docker](https://www.docker.com/get-started)

## Estrutura do Projeto


/
|-- app/                # Código-fonte da aplicação
|-- requirements.txt    # Dependências do projeto
|-- Dockerfile          # Configuração do contêiner Docker
|-- docker-compose.yml  # (Opcional) Configuração para múltiplos serviços
|-- README.md           # Documentação do projeto


## Construção e Execução com Docker

### 1. Construir a imagem Docker

Execute o seguinte comando no terminal dentro do diretório do projeto:


docker build -t nome-do-app .


### 2. Executar o contêiner


docker run -p 5000:5000 nome-do-app

A aplicação estará disponível em http://localhost:5000.

## Dockerfile

O projeto utiliza o seguinte 'Dockerfile' para criar a imagem:


FROM python:3.9.21
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . /app/
CMD ["gunicorn", "--bind", "0.0.0.0:5000", "app:app"]


## Encerrando o Contêiner

Para parar o contêiner em execução, encontre o ID com:

docker ps

E então pare o contêiner com:

docker stop <container_id>


## Possíveis Melhorias

- Adicionar um docker-compose.yml para facilitar a execução.
- Utilizar um arquivo .env para variáveis de ambiente.
- Criar testes automatizados para garantir a estabilidade da aplicação.

## Licença

Este projeto é distribuído sob a licença MIT.

gi