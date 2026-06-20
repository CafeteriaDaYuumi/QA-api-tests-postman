# Casos de Teste

## Projeto

Testes de API REST com Postman — Restful Booker

---

## CT001 — Gerar Token com Credenciais Válidas

**Endpoint:** POST /auth

**Pré-condição:** API disponível.

**Massa de Dados:**

```json
{
  "username": "admin",
  "password": "password123"
}
```

**Passos:**

1. Enviar requisição POST para `/auth`.
2. Informar credenciais válidas.
3. Executar a requisição.

**Resultado Esperado:**

* Retornar HTTP 200.
* Retornar token de autenticação válido.
* O campo token não deve estar vazio.

---

## CT002 — Gerar Token com Credenciais Inválidas

**Endpoint:** POST /auth

**Massa de Dados:**

```json
{
  "username": "usuario_invalido",
  "password": "senha_invalida"
}
```

**Resultado Esperado:**

* Retornar HTTP 200.
* Retornar mensagem de falha na autenticação.

---

## CT003 — Listar Todas as Reservas Cadastradas

**Endpoint:** GET /booking

**Resultado Esperado:**

* Retornar HTTP 200.
* Retornar lista de reservas cadastradas.
* Retornar ao menos um campo `bookingid`.

---

## CT004 — Criar Reserva com Dados Válidos

**Endpoint:** POST /booking

**Massa de Dados:**

```json
{
  "firstname": "Victor",
  "lastname": "Hugo",
  "totalprice": 350,
  "depositpaid": true,
  "bookingdates": {
    "checkin": "2026-07-01",
    "checkout": "2026-07-05"
  },
  "additionalneeds": "Breakfast"
}
```

**Resultado Esperado:**

* Retornar HTTP 200.
* Criar uma nova reserva.
* Retornar o ID da reserva criada.
* Retornar os dados enviados no corpo da resposta.

---

## CT005 — Consultar Reserva Existente por ID

**Endpoint:** GET /booking/{id}

**Pré-condição:**

* Executar CT004 para criar uma reserva válida e armazenar o bookingID retornado pela API.

**Resultado Esperado:**

* Retornar HTTP 200.
* Retornar os dados da reserva consultada.

---

## CT006 — Consultar Reserva Inexistente por ID

**Endpoint:** GET /booking/{id}

**Massa de Dados:** ID inexistente.

**Resultado Esperado:**

* Retornar HTTP 404.
* Não retornar dados de reserva.

---

## CT007 — Criar Reserva com Campos Obrigatórios Ausentes

**Endpoint:** POST /booking

**Massa de Dados:**

```json
{
  "firstname": "Victor"
}
```

**Resultado Esperado:**

* Retornar erro de validação ou comportamento inconsistente documentado.
* Registrar defeito caso a API aceite dados incompletos.

---

## CT008 — Criar Reserva com Formato de Data Inválido

**Endpoint:** POST /booking

**Massa de Dados:**

```json
{
  "firstname": "Victor",
  "lastname": "Hugo",
  "totalprice": 350,
  "depositpaid": true,
  "bookingdates": {
    "checkin": "data-invalida",
    "checkout": "2026-07-05"
  },
  "additionalneeds": "Breakfast"
}
```

**Resultado Esperado:**

* Retornar erro de validação.
* Registrar defeito caso a API aceite data inválida.

---

## CT009 — Atualizar Reserva Existente com Token Válido

**Endpoint:** PUT /booking/{id}

**Pré-condição:**

* Executar CT001 para gerar um token válido.
* Executar CT004 para criar uma reserva válida e armazenar o bookingID retornado pela API.

**Resultado Esperado:**

* Retornar HTTP 200.
* Atualizar os dados da reserva.
* Retornar os dados atualizados.

---

## CT010 — Atualizar Reserva Existente sem Token

**Endpoint:** PUT /booking/{id}

**Pré-condição:**

* Executar CT004 para criar uma reserva válida.

**Resultado Esperado:**

* Retornar HTTP 403.
* Não permitir alteração sem autenticação.

---

## CT011 — Atualizar Reserva Inexistente

**Endpoint:** PUT /booking/{id}

**Pré-condição:**

* Possuir token de autenticação válido.

**Resultado Esperado:**

* Retornar erro para ID inexistente.
* Não criar nova reserva indevidamente.

---

## CT012 — Excluir Reserva Existente com Token Válido

**Endpoint:** DELETE /booking/{id}

**Pré-condição:**

* Executar CT001 para gerar um token válido.
* Executar CT004 para criar uma reserva válida e armazenar o bookingID retornado pela API.

**Resultado Esperado:**

* Retornar HTTP 201.
* Excluir a reserva informada.

---

## CT013 — Excluir Reserva Existente sem Token

**Endpoint:** DELETE /booking/{id}

**Pré-condição:**

* Executar CT004 para criar uma reserva válida.
* Não informar token de autenticação.

**Resultado Esperado:**

* Retornar HTTP 403.
* Não permitir exclusão sem autenticação.

---

## CT014 — Excluir Reserva Inexistente

**Endpoint:** DELETE /booking/{id}

**Pré-condição:**

* Possuir token de autenticação válido.

**Resultado Esperado:**

* Retornar erro para ID inexistente.
* Não excluir nenhum registro válido.

---

## CT015 — Validar Contrato JSON da Resposta de Criação de Reserva

**Endpoint:** POST /booking

**Resultado Esperado:**

A resposta deve conter os campos obrigatórios do contrato JSON:

* bookingid
* booking
* firstname
* lastname
* totalprice
* depositpaid
* bookingdates
* additionalneeds

---

## CT016 — Validar Contrato JSON da Consulta de Reserva por ID

**Endpoint:** GET /booking/{id}

**Resultado Esperado:**

A resposta deve conter todos os campos obrigatórios definidos no contrato JSON da consulta de reserva:

* firstname
* lastname
* totalprice
* depositpaid
* bookingdates
* additionalneeds

---

## CT017 — Validar Código HTTP para Requisições Bem-Sucedidas

**Escopo:** Cenários positivos.

**Resultado Esperado:**

* CT001 → HTTP 200
* CT003 → HTTP 200
* CT004 → HTTP 200
* CT005 → HTTP 200
* CT009 → HTTP 200
* CT012 → HTTP 201

---

## CT018 — Validar Tratamento de Erro para Requisições Inválidas

**Escopo:** Cenários negativos.

**Resultado Esperado:**

* CT002 → Falha de autenticação.
* CT006 → HTTP 404.
* CT007 → Erro ou comportamento documentado.
* CT008 → Erro ou comportamento documentado.
* CT010 → HTTP 403.
* CT011 → Erro para ID inexistente.
* CT013 → HTTP 403.
* CT014 → Erro para ID inexistente.

---

## Observações

As evidências dos testes deverão ser registradas por meio de capturas de tela e resultados obtidos no Postman.

Os testes utilizam variáveis de ambiente para gerenciamento do token de autenticação e do bookingID gerado dinamicamente durante a execução.

Qualquer divergência entre o resultado esperado e o resultado obtido deverá ser registrada no documento Registro_de_Defeitos.md.
