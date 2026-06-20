# BUG001 - API Aceita Criação de Reserva com Data Inválida

## Resumo

A API Restful Booker permite a criação de reservas contendo datas em formato inválido no campo `checkin`, retornando sucesso na operação e armazenando dados inconsistentes.

---

## Informações do Defeito

| Campo            | Valor                                           |
| ---------------- | ----------------------------------------------- |
| ID               | BUG001                                          |
| Título           | API aceita criação de reserva com data inválida |
| Caso de Teste    | CT008                                           |
| Módulo           | Reservas                                        |
| Endpoint         | POST /booking                                   |
| Data de Registro | 20/06/2026                                      |
| Reportado por    | Victor Hugo                                     |
| Severidade       | Média                                           |
| Prioridade       | Média                                           |
| Status           | Aberto                                          |

---

## Descrição

Durante a execução do caso de teste CT008 foi identificado que o endpoint de criação de reservas não realiza validação adequada dos campos de data.

Ao informar uma data inválida no campo `checkin`, a API processa a requisição normalmente, retorna sucesso na operação e cria a reserva.

Esse comportamento permite a persistência de informações inconsistentes e compromete a integridade dos dados armazenados.

---

## Ambiente de Teste

**Sistema:** Restful Booker

**URL Base**

```text
https://restful-booker.herokuapp.com
```

**Ferramenta Utilizada**

```text
Postman
```

**Método HTTP**

```text
POST
```

**Endpoint**

```text
/booking
```

---

## Pré-condições

* API disponível para acesso.
* Endpoint de reservas operacional.
* Requisição configurada com Content-Type application/json.

---

## Passos para Reprodução

### Passo 1

Enviar uma requisição POST para:

```text
/booking
```

### Passo 2

Utilizar o seguinte payload:

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

### Passo 3

Executar a requisição.

### Passo 4

Analisar o código HTTP retornado e o conteúdo da resposta.

---

## Resultado Esperado

A API deve validar o formato dos campos de data antes da criação da reserva.

A requisição deve ser rejeitada retornando um código de erro apropriado, como:

```text
400 Bad Request
```

ou

```text
422 Unprocessable Entity
```

Nenhuma reserva deve ser criada.

---

## Resultado Obtido

A API retornou:

```text
HTTP 200 OK
```

A reserva foi criada com sucesso.

O valor enviado:

```json
"checkin": "data-invalida"
```

foi convertido internamente para:

```json
"checkin": "0NaN-aN-aN"
```

permitindo o armazenamento de um valor inválido.

---

## Impacto

* Permite cadastro de dados inconsistentes.
* Compromete a integridade dos registros.
* Pode causar falhas em integrações futuras.
* Pode gerar erros em relatórios e consultas dependentes de datas válidas.
* Demonstra ausência de validação de entrada para campos críticos.

---

## Evidências

### Evidência 01 - Corpo da Requisição

```text
docs/Defeitos/Evidencias/BUG001/BUG001_01_Body_Enviado.png
```

Payload enviado contendo valor inválido para o campo `checkin`.

### Evidência 02 - Resposta da API

```text
docs/Defeitos/Evidencias/BUG001/BUG001_02_Resposta_API.png
```

Retorno HTTP 200 OK com criação da reserva.

### Evidência 03 - Headers da Requisição

```text
docs/Defeitos/Evidencias/BUG001/BUG001_03_Headers_Requisicao.png
```

Comprovação do envio correto da requisição utilizando Content-Type application/json.

---

## Critério de Correção

O defeito será considerado corrigido quando:

* Datas inválidas forem rejeitadas pela API.
* A API retornar código HTTP compatível com erro de validação.
* Nenhuma reserva for criada quando os campos de data estiverem fora do formato esperado.
* Os testes CT008 forem executados novamente com sucesso.

---

## Observações

Embora a Restful Booker seja uma API utilizada para fins educacionais e demonstração, o comportamento observado diverge das práticas recomendadas para validação de dados em APIs REST utilizadas em ambientes corporativos.
