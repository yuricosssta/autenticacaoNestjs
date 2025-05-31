# Autenticação JWT com NestJS

Este projeto é uma API de autenticação utilizando [NestJS](https://nestjs.com/) e JWT.

## Sumário

- [Descrição](#descrição)
- [Pré-requisitos](#pré-requisitos)
- [Instalação](#instalação)
- [Configuração](#configuração)
- [Execução](#execução)
- [Testes](#testes)
- [Uso da API](#uso-da-api)
- [Exemplo de uso com Postman](#exemplo-de-uso-com-postman)
- [Licença](#licença)

---

## Descrição

API para autenticação de usuários utilizando JWT. Permite login e acesso a rotas protegidas.

## Pré-requisitos

- Node.js (v18+ recomendado)
- npm ou yarn

## Instalação

```bash
git clone https://github.com/yuricosssta/autenticacaoNestjs.git
cd autenticacaoNestjs
npm install
```

## Configuração

Crie um arquivo `.env` na raiz do projeto com o seguinte conteúdo:

```env
PORT=3001

# Configurações do MongoDB
MONGO_URI=seu_mongo_uri
MONGO_INITDB_ROOT_USERNAME=seu_usuario
MONGO_INITDB_ROOT_PASSWORD=sua_senha

# Configurações da Aplicação
JWT_SECRET=sua_chave_secreta
JWT_EXPIRES_IN=3600s
NODE_ENV=development
```

## Execução

```bash
# Modo desenvolvimento
npm run start:dev

# Modo produção
npm run start:prod
```

A API estará disponível em `http://localhost:3001`.

## Testes

```bash
# Testes unitários
npm run test

# Testes end-to-end
npm run test:e2e
```

## Uso da API

### Login

- **Endpoint:** `POST /auth/login`
- **Body:**
  ```json
  {
    "username": "john",
    "password": "changeme"
  }
  ```
- **Resposta:**
  ```json
  {
    "access_token": "seu_token_jwt"
  }
  ```

### Acesso a rota protegida

- **Endpoint:** `GET /auth/profile`
- **Headers:**
  ```
  Authorization: Bearer seu_token_jwt
  ```
- **Resposta:**
  ```json
  {
    "sub": 1,
    "username": "john",
    "iat": 123456789,
    "exp": 123456999
  }
  ```

## Exemplo de uso com Postman

1. Faça login em `/auth/login` com o corpo JSON acima.
2. Copie o `access_token` retornado.
3. Em uma nova requisição GET para `/auth/profile`, adicione o header:
   ```
   Authorization: Bearer <access_token>
   ```
4. Você receberá os dados do usuário autenticado.

## Licença

MIT

---

> Projeto desenvolvido com [NestJS](https://nestjs.com/).