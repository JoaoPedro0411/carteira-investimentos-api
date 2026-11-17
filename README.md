# API de carteira de investimentos

API REST acadêmica para uma aplicação de carteira de investimentos. Este repositório público é uma cópia com histórico novo, preparada para demonstrar uma API em camadas com autenticação, persistência relacional, regras de negócio e integração com cotações externas.

> **Segurança:** credenciais reais foram removidas desta cópia. As variáveis necessárias estão listadas em `.env.example` com valores demonstrativos; configure suas próprias credenciais em um arquivo local `.env`, que não deve ser versionado.

## Funcionalidades

- Cadastro e gerenciamento de usuários
- Autenticação local e OAuth do GitHub com JWT
- Depósitos e retiradas de saldo
- Compra e venda de ativos e atualização da carteira
- Histórico de transações e cálculo de rentabilidade
- Consulta de ativos e cotações pela integração Brapi
- Persistência MySQL com Sequelize

## Tecnologias

Node.js, Express, Sequelize, MySQL, Passport, JWT, bcrypt, Axios, dotenv e express-validator.

## Organização

```text
src/
├── config/       # Banco de dados e estratégias de autenticação
├── controllers/  # Camada HTTP
├── middlewares/  # Autenticação JWT
├── models/       # Modelos Sequelize
├── routes/       # Rotas da API
└── services/     # Regras de negócio e integração com a Brapi
index.js          # Inicialização do servidor
```

## Principais rotas

| Método | Rota | Finalidade |
| --- | --- | --- |
| POST | `/auth/login` | Login local |
| GET | `/auth/github/login` | Inicia OAuth do GitHub |
| GET | `/auth/github/callback` | Callback OAuth |
| POST | `/auth/verify-token` | Verifica JWT |
| POST | `/users/register` | Cadastro |
| POST | `/portfolio/buy` | Registra compra |
| POST | `/portfolio/sell` | Registra venda |
| GET | `/portfolio/portfolio` | Consulta carteira autenticada |
| GET | `/portfolio/history` | Consulta histórico autenticado |
| GET | `/portfolio/return` | Calcula rentabilidade |
| GET | `/portfolio/detailed-assets` | Consulta ativos detalhados |

As operações de carteira exigem autenticação JWT. Consulte as rotas e controladores para os demais endpoints de usuário.

## Executar localmente

Requisitos: Node.js, MySQL e credenciais próprias para as integrações externas que desejar testar.

```bash
npm install
cp .env.example .env
```

Preencha `.env` com os dados do seu ambiente e inicie:

```bash
npm run dev
```

Para iniciar sem nodemon, use `npm start`. No Windows, copie o arquivo pelo Explorador ou use `Copy-Item .env.example .env` no PowerShell.

## Variáveis de ambiente

O arquivo `.env.example` lista as variáveis de servidor, MySQL, JWT, OAuth e Brapi. Os valores nele são placeholders. Nunca coloque tokens ou senhas reais no Git.

## Escopo acadêmico

Este projeto demonstra conceitos de desenvolvimento backend e **não é um serviço financeiro pronto para produção**. Use dados de demonstração. Validação, tratamento de erros, cobertura de testes e revisão de segurança precisam ser ampliados antes de qualquer uso real.
