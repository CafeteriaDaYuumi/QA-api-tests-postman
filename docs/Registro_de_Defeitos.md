# Registro de Defeitos

## Projeto

Testes de API REST com Postman — Restful Booker

## Objetivo

Documentar os defeitos identificados durante a execução dos testes funcionais, validações de contrato JSON e cenários negativos da API Restful Booker.

---

## BUG001

**Título:**
API aceita criação de reserva com formato de data inválido

**ID do Caso de Teste:**
CT008

**Severidade:**
Média

**Prioridade:**
Média

**Status:**
Aberto

**Data da Identificação:**
20/06/2026

### Descrição

A API permite a criação de reservas mesmo quando o campo de data é enviado em formato inválido, sem realizar validação adequada dos dados recebidos.

### Pré-condições

* API disponível para acesso.
* Endpoint de criação de reservas operacional.

### Passos para Reproduzir

1. Enviar uma requisição POST para `/booking`.
2. Informar uma data inválida no campo `checkin`.
3. Enviar a requisição.

### Resultado Esperado

A API deve rejeitar a requisição retornando HTTP 400 (Bad Request) ou HTTP 422 (Unprocessable Entity).

### Resultado Obtido

A API retornou HTTP 200 (OK) e criou a reserva normalmente.

### Evidência

* CT008.png
* Resposta HTTP 200 OK
* Resultado da execução no Postman

### Observações

O defeito pode comprometer a integridade dos dados armazenados na aplicação.

---

## BUG002

**Título:**
API retorna erro interno ao receber campos obrigatórios ausentes

**ID do Caso de Teste:**
CT007

**Severidade:**
Baixa

**Prioridade:**
Baixa

**Status:**
Aberto

**Data da Identificação:**
20/06/2026

### Descrição

Ao receber uma requisição de criação de reserva sem todos os campos obrigatórios, a API retorna erro interno do servidor em vez de informar erro de validação ao cliente.

### Pré-condições

* API disponível para acesso.
* Endpoint de criação de reservas operacional.

### Passos para Reproduzir

1. Enviar uma requisição POST para `/booking`.
2. Informar apenas o campo `firstname`.
3. Enviar a requisição.

### Resultado Esperado

A API deve retornar HTTP 400 (Bad Request) ou HTTP 422 (Unprocessable Entity), informando dados obrigatórios ausentes.

### Resultado Obtido

A API retornou HTTP 500 (Internal Server Error).

### Evidência

* CT007.png
* Resposta HTTP 500 Internal Server Error
* Resultado da execução no Postman

### Observações

Embora o erro seja tratado pelo servidor, a resposta não informa adequadamente ao cliente quais campos são obrigatórios.

---

## Resumo dos Defeitos

| ID     | Título                                                           | Severidade | Prioridade | Status |
| ------ | ---------------------------------------------------------------- | ---------- | ---------- | ------ |
| BUG001 | API aceita criação de reserva com formato de data inválido       | Média      | Média      | Aberto |
| BUG002 | API retorna erro interno ao receber campos obrigatórios ausentes | Baixa      | Baixa      | Aberto |

---

## Legenda

### Severidade

* Crítica → Impede o funcionamento da funcionalidade.
* Alta → Funcionalidade apresenta falha grave.
* Média → Funcionalidade opera com comportamento incorreto.
* Baixa → Impacto reduzido ou apenas visual/documental.

### Prioridade

* Urgente → Correção imediata.
* Alta → Corrigir o quanto antes.
* Média → Corrigir em próxima versão.
* Baixa → Correção opcional ou futura.