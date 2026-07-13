# Teste Técnico – Desenvolvedor(a) Full Stack (Laravel + Vue.js ou React + IA)

## Objetivo

Este desafio tem como objetivo avaliar sua capacidade de desenvolver uma aplicação Full Stack integrando uma API de Inteligência Artificial para extração estruturada de dados a partir de um documento PDF. A persistência dos dados poderá ser realizada utilizando PostgreSQL (preferencialmente) ou MySQL.

Serão avaliados principalmente:

- Organização do código;
- Arquitetura da solução;
- Integração com APIs externas;
- Persistência de dados;
- Boas práticas de desenvolvimento;
- Qualidade da implementação.

O foco não está apenas na entrega das funcionalidades, mas também na forma como a solução foi construída.

---

# Cenário

Sua equipe precisa automatizar a importação de clientes recebidos em formato PDF.

Desenvolva uma aplicação capaz de receber um arquivo PDF contendo uma lista de clientes e utilizar um modelo de Inteligência Artificial para extrair as informações presentes no documento.

Após a extração, os clientes deverão ser persistidos em um banco de dados relacional. O candidato poderá optar por PostgreSQL (preferencialmente) ou MySQL.

O PDF será utilizado apenas durante o processamento da importação, não sendo necessário armazená-lo.

---

# Backend

## Stack

- PHP 8+
- Laravel 10+
- PostgreSQL (preferencialmente) ou MySQL

## Processamento

1. Receber o arquivo PDF.
2. Enviar o documento para um serviço de IA.
3. Solicitar a extração dos clientes em formato estruturado.
4. Validar o retorno.
5. Persistir os clientes no banco de dados.
6. Retornar o resultado da importação.

## Integração com IA

É permitido utilizar qualquer provedor compatível (OpenAI, Gemini, Claude, OpenRouter, Groq, Ollama ou outro).

A chave da API deverá ser configurada por variável de ambiente.

A aplicação deverá tratar timeout, erros de comunicação, respostas inválidas e falhas durante a persistência.

### Regra de Desenvolvimento

- **Não é permitida a utilização de expressões regulares (Regex) para realizar a extração dos dados contidos no PDF.**
- **É obrigatória a utilização de uma API de Inteligência Artificial para realizar a extração estruturada das informações presentes no documento.**
- Regex poderá ser utilizada apenas para validações ou formatações complementares após o retorno da IA, não para identificar ou extrair os dados do documento.

---

# Persistência

Estrutura mínima esperada da entidade **Cliente**:

- id
- name
- cpf
- email
- phone
- city
- state
- zipcode
- created_at

---

# Schema esperado

```json
{
  "customers": [
    {
      "name": "string",
      "cpf": "string",
      "email": "string",
      "phone": "string",
      "city": "string",
      "state": "string",
      "zipcode": "string"
    }
  ]
}
```

## Regras

- A chave raiz deverá ser `customers`;
- Cada objeto representa um cliente encontrado no documento;
- A ordem dos clientes deverá ser preservada;
- Não deverão existir campos adicionais;
- Campos ausentes deverão ser retornados como `null`.

---

# API

## Importação

```http
POST /customers/import
```

## Listagem

```http
GET /customers
```

---

# Frontend

Escolha uma das opções:

- Vue.js 3 + TypeScript
- React + TypeScript

Funcionalidades:

- Upload do PDF;
- Visualização do resultado da importação;
- Listagem dos clientes cadastrados.

---

# Docker

Disponibilizar um ambiente Docker contendo:

- Backend
- Frontend
- PostgreSQL (preferencialmente) ou MySQL

Utilizar `docker-compose.yml`.

---

# Documento de Entrada

Será disponibilizado um PDF contendo uma lista fictícia de clientes.

A aplicação deverá utilizar IA para extrair os dados presentes no documento e persisti-los no banco de dados.

---

# Diferenciais (Opcional)

- Pesquisa por nome, CPF ou e-mail;
- Paginação;
- Prevenção de clientes duplicados;
- Processamento assíncrono utilizando filas;
- Barra de progresso durante a importação;
- Testes automatizados;
- Documentação da API (Swagger/OpenAPI);
- Structured Outputs, Function Calling ou JSON Schema;
- Transações durante a importação;
- Suporte a múltiplos provedores de IA.

---

# README

O projeto deverá conter um README explicando:

- como executar a aplicação;
- como configurar a chave da API;
- arquitetura da solução;
- decisões técnicas;
- limitações da implementação;
- melhorias futuras.

Caso alguma funcionalidade não seja concluída, explique no README como faria sua implementação.

---

# Critérios de Avaliação

## Backend

- Organização do código;
- Arquitetura;
- Integração com APIs externas;
- Persistência dos dados;
- Tratamento de erros;
- Boas práticas de desenvolvimento.

## Frontend

- Organização dos componentes;
- Clareza da implementação;
- Integração com a API;
- Responsividade.

## Gerais

- Docker;
- Documentação;
- Legibilidade do código;
- Estrutura do projeto.

---

# Entrega

- Deve ser entregue um arquivo .zip do projeto ou o link para um repositório **público**, caso o projeto seja versionado no Git.

---

# Observações

- Não é obrigatório utilizar um provedor específico de IA.
- O objetivo não é avaliar conhecimento prévio sobre um serviço específico, mas sim a capacidade de integrar uma API externa e estruturar uma solução.
- É permitido utilizar SDKs oficiais ou bibliotecas disponibilizadas pelos provedores de IA.
- O documento PDF disponibilizado contém dados totalmente fictícios e deve ser utilizado exclusivamente para fins de avaliação técnica.
