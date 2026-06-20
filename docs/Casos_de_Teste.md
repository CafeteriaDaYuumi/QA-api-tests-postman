# Casos de Teste

## Projeto

Testes de API REST com Postman — Restful Booker

---

## CT001 — Gerar token com credenciais válidas

**Endpoint:** POST /auth

**Pré-condição:** API disponível.

**Massa de dados:**

```json
{
  "username": "admin",
  "password": "password123"
}
```

**Passos:**

1. Enviar requisição POST para `/auth`.
2. Informar credenciais válidas.
3. Executar a requisição no Postman.

**Resultado esperado:**

* Retornar HTTP 200.
* Retornar um token de autenticação válido.

---

## CT002 — Gerar token com credenciais inválidas

**Endpoint:** POST /auth

**Massa de dados:**

```json
{
  "username": "usuario_invalido",
  "password": "senha_invalida"
}
```

**Resultado esperado:**

* Retornar HTTP 200.
* Retornar mensagem de falha na autenticação.

---

## CT003 — Listar reservas cadastradas

**Endpoint:** GET /booking

**Resultado esperado:**

* Retornar HTTP 200.
* Retornar lista de reservas cadastradas.

---

## CT004 — Consultar reserva existente por ID

**Endpoint:** GET /booking/{id}

**Pré-condição:** Existir uma reserva cadastrada.

**Resultado esperado:**

* Retornar HTTP 200.
* Retornar os dados da reserva consultada.

---

## CT005 — Consultar reserva inexistente

**Endpoint:** GET /booking/{id}

**Massa de dados:** ID inexistente.

**Resultado esperado:**

* Retornar HTTP 404.
* Não retornar dados de reserva.

---

## CT006 — Criar reserva com dados válidos

**Endpoint:** POST /booking

**Massa de dados:**

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

**Resultado esperado:**

* Retornar HTTP 200.
* Criar uma nova reserva.
* Retornar o ID da reserva criada.
* Retornar os dados enviados no corpo da resposta.

---

## CT007 — Criar reserva com campos obrigatórios ausentes

**Endpoint:** POST /booking

**Massa de dados:**

```json
{
  "firstname": "Victor"
}
```

**Resultado esperado:**

* Retornar erro ou comportamento inconsistente documentado.
* Registrar defeito caso a API aceite dados incompletos.

---

## CT008 — Criar reserva com formato de data inválido

**Endpoint:** POST /booking

**Massa de dados:**

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

**Resultado esperado:**

* Retornar erro de validação.
* Registrar defeito caso a API aceite data inválida.

---

## CT009 — Atualizar reserva existente com token válido

**Endpoint:** PUT /booking/{id}

**Pré-condição:**

* Existir uma reserva cadastrada.
* Possuir token de autenticação válido.

**Resultado esperado:**

* Retornar HTTP 200.
* Atualizar os dados da reserva.
* Retornar os dados atualizados.

---

## CT010 — Atualizar reserva sem token

**Endpoint:** PUT /booking/{id}

**Pré-condição:** Existir uma reserva cadastrada.

**Resultado esperado:**

* Retornar HTTP 403.
* Não permitir alteração sem autenticação.

---

## CT011 — Atualizar reserva inexistente

**Endpoint:** PUT /booking/{id}

**Pré-condição:** Possuir token válido.

**Resultado esperado:**

* Retornar erro para ID inexistente.
* Não criar nova reserva indevidamente.

---

## CT012 — Excluir reserva existente com token válido

**Endpoint:** DELETE /booking/{id}

**Pré-condição:**

* Existir uma reserva cadastrada.
* Possuir token de autenticação válido.

**Resultado esperado:**

* Retornar HTTP 201.
* Excluir a reserva informada.

---

## CT013 — Excluir reserva sem token

**Endpoint:** DELETE /booking/{id}

**Resultado esperado:**

* Retornar HTTP 403.
* Não permitir exclusão sem autenticação.

---

## CT014 — Excluir reserva inexistente

**Endpoint:** DELETE /booking/{id}

**Pré-condição:** Possuir token válido.

**Resultado esperado:**

* Retornar erro para ID inexistente.
* Não excluir nenhum registro válido.

---

## CT015 — Validar contrato JSON da criação de reserva

**Endpoint:** POST /booking

**Resultado esperado:**

A resposta deve conter:

```json
{
  "bookingid": "number",
  "booking": {
    "firstname": "string",
    "lastname": "string",
    "totalprice": "number",
    "depositpaid": "boolean",
    "bookingdates": {
      "checkin": "string",
      "checkout": "string"
    },
    "additionalneeds": "string"
  }
}
```

---

## CT016 — Validar contrato JSON da consulta de reserva

**Endpoint:** GET /booking/{id}

**Resultado esperado:**

A resposta deve conter:

```json
{
  "firstname": "string",
  "lastname": "string",
  "totalprice": "number",
  "depositpaid": "boolean",
  "bookingdates": {
    "checkin": "string",
    "checkout": "string"
  },
  "additionalneeds": "string"
}
```

---

## Observações

Os resultados obtidos durante a execução deverão ser registrados por meio de evidências no Postman.

Caso o comportamento real seja diferente do resultado esperado, o desvio deverá ser documentado no Registro de Defeitos.
