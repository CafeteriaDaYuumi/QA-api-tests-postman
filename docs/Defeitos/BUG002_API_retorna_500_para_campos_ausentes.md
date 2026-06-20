# BUG002 - API Retorna Erro 500 ao Receber Campos Obrigatórios Ausentes

## Resumo

A API Restful Booker retorna erro interno do servidor (HTTP 500) ao receber uma requisição de criação de reserva contendo apenas parte dos campos obrigatórios, em vez de retornar um erro de validação apropriado ao cliente.

---

## Informações do Defeito

| Campo            | Valor                                                  |
| ---------------- | ------------------------------------------------------ |
| ID               | BUG002                                                 |
| Título           | API retorna erro 500 para campos obrigatórios ausentes |
| Caso de Teste    | CT007                                                  |
| Módulo           | Reservas                                               |
| Endpoint         | POST /booking                                          |
| Data de Registro | 20/06/2026                                             |
| Reportado por    | Victor Hugo                                            |
| Severidade       | Baixa                                                  |
| Prioridade       | Baixa                                                  |
| Status           | Aberto                                                 |

---

## Descrição

Durante a execução do caso de teste CT007 foi identificado que o endpoint de criação de reservas não trata adequadamente requisições com campos obrigatórios ausentes.

Ao enviar apenas o campo `firstname`, a API retorna um erro interno do servidor (HTTP 500), expondo uma falha interna em vez de informar ao consumidor da API que os dados enviados são insuficientes para a criação da reserva.

Esse comportamento dificulta a identificação do problema pelo cliente e não segue as boas práticas de tratamento de erros em APIs REST.

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
  "firstname": "Victor"
}
```

### Passo 3

Executar a requisição.

### Passo 4

Analisar o código HTTP retornado e o conteúdo da resposta.

---

## Resultado Esperado

A API deve validar a presença dos campos obrigatórios antes do processamento da requisição.

A requisição deve ser rejeitada retornando um código de erro apropriado, como:

```text
400 Bad Request
```

ou

```text
422 Unprocessable Entity
```

Além disso, a resposta deve informar quais campos obrigatórios estão ausentes.

Nenhuma reserva deve ser criada.

---

## Resultado Obtido

A API retornou:

```text
500 Internal Server Error
```

Sem informar adequadamente quais campos obrigatórios estavam ausentes.

Embora a reserva não tenha sido criada, a API expôs um erro interno do servidor em vez de retornar uma mensagem de validação apropriada.

---

## Impacto

* Exposição desnecessária de erro interno do servidor.
* Dificulta a identificação do problema pelo consumidor da API.
* Indica falha ou ausência de validação de entrada.
* Pode gerar comportamento inesperado em integrações.
* Não segue boas práticas de tratamento de erros para APIs REST.

---

## Evidências

### Evidência 01 - Corpo da Requisição

```text
docs/Defeitos/Evidencias/BUG002/BUG002_01_Body_Enviado.png
```

Payload enviado contendo apenas o campo `firstname`.

### Evidência 02 - Resposta da API

```text
docs/Defeitos/Evidencias/BUG002/BUG002_02_Resposta_API.png
```

Retorno HTTP 500 Internal Server Error.

### Evidência 03 - Headers da Requisição

```text
docs/Defeitos/Evidencias/BUG002/BUG002_03_Headers_Requisicao.png
```

Comprovação do envio correto da requisição utilizando Content-Type application/json.

---

## Critério de Correção

O defeito será considerado corrigido quando:

* A API validar os campos obrigatórios antes do processamento.
* Requisições incompletas retornarem HTTP 400 ou HTTP 422.
* A resposta informar claramente os campos ausentes.
* O caso de teste CT007 for executado novamente sem ocorrência de erro interno.

---

## Observações

Embora a Restful Booker seja uma API utilizada para fins educacionais e demonstração, o comportamento observado diverge das práticas recomendadas para validação de entrada e tratamento de erros em APIs REST utilizadas em ambientes corporativos.

O defeito foi reproduzido com sucesso durante a execução do CT007 e possui evidências suficientes para análise e correção.

