### Desafio de Microsserviços com Docker

A tecnologia de Containers está revolucionando o mundo da TI ao simplificar a gestão de ambientes de desenvolvimento e otimizar o uso de recursos. Com o Docker, você pode criar uma estrutura de Microsserviços seguindo as melhores práticas do mercado. Este desafio visa proporcionar essa experiência e aumentar seu portfólio no GitHub.

#### Pré-requisitos:
- Conhecimentos básicos em Linux, Docker e AWS.

### Descrição do Desafio

#### Passos para Resolver o Desafio:

1. **Preparação do Ambiente**
   - **Instalação do Docker**: Siga as instruções oficiais [aqui](https://docs.docker.com/get-docker/).
   - **Configuração da AWS CLI**: Instale e configure conforme instruções [aqui](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html).
   - **Configurações do GitHub**: Crie e clone um repositório para armazenar seu projeto.

2. **Criação da Estrutura de Microsserviços**
   - **Definição dos Microsserviços**: Identifique quais serviços são necessários (e.g., autenticação, dados, API).
   - **Criação dos Dockerfiles**: Cada serviço deve ter seu próprio `Dockerfile` para definir sua construção.
   ```Dockerfile
   FROM node:14
   WORKDIR /app
   COPY package*.json ./
   RUN npm install
   COPY . .
   EXPOSE 3000
   CMD ["node", "index.js"]
   ```
   - **Configuração do Docker Compose**: Use o Docker Compose para orquestrar os serviços.
   ```yaml
   version: '3.8'
   services:
     service1:
       build: ./service1
       ports:
         - "3001:3001"
     service2:
       build: ./service2
       ports:
         - "3002:3002"
   ```

3. **Implementação das Melhores Práticas**
   - **Melhorias e Boas Práticas**: Adicione logs, use variáveis de ambiente e implemente health checks.
   - **Documentação**: Adicione uma documentação detalhada no repositório.
   ```markdown
   # Projeto de Microsserviços com Docker

   ## Descrição
   Este projeto implementa uma arquitetura de microsserviços utilizando Docker, seguindo as melhores práticas do mercado.

   ## Serviços
   - **Service1**: Serviço de autenticação
   - **Service2**: Serviço de dados

   ## Como Executar
   1. Clone o repositório: `git clone <URL_DO_REPOSITORIO>`
   2. Navegue até a pasta do projeto: `cd <NOME_DO_REPOSITORIO>`
   3. Execute o Docker Compose: `docker-compose up --build`
   ```

4. **Deploy na AWS**
   - **Configuração do ECS (Elastic Container Service)**: Crie um cluster, configure tarefas e serviços.
   - **Automatização com CI/CD**: Use GitHub Actions para automatizar o build e deploy.
   ```yaml
   name: CI/CD Pipeline

   on:
     push:
       branches:
         - main

   jobs:
     build:
       runs-on: ubuntu-latest
       steps:
         - name: Checkout code
           uses: actions/checkout@v2
         - name: Set up Docker Buildx
           uses: docker/setup-buildx-action@v1
         - name: Login to DockerHub
           uses: docker/login-action@v1
           with:
             username: ${{ secrets.DOCKER_USERNAME }}
             password: ${{ secrets.DOCKER_PASSWORD }}
         - name: Build and push
           uses: docker/build-push-action@v2
           with:
             push: true
             tags: user/repo:latest
   ```

5. **Melhorias e Personalizações**
   - **Melhoria da Estrutura do Projeto**: Refatore o código para otimizar performance e manutenção.
   - **Funcionalidades Extras**: Adicione funcionalidades como autenticação OAuth, caching, etc.

6. **Publicação e Compartilhamento**
   - **Compartilhe o Repositório**: Atualize o README.md e compartilhe o repositório no GitHub.
   - **Demonstre o Projeto**: Crie uma breve demonstração do projeto funcionando.

### Estrutura de Pastas

```
.
├── service1
│   ├── Dockerfile
│   ├── index.js
│   └── package.json
├── service2
│   ├── Dockerfile
│   ├── index.js
│   └── package.json
├── docker-compose.yml
└── README.md
```

Seguindo esses passos, você completará o desafio com uma estrutura de microsserviços robusta e bem documentada. Em caso de dúvidas, sinta-se à vontade para perguntar!
