# Plano de Testes

## 1. Objetivo

Este documento tem como objetivo definir o planejamento e a estratégia de testes para a API Restful Booker, utilizando a ferramenta Postman para validação funcional dos endpoints disponibilizados pela aplicação.

Os testes serão executados com foco na validação dos métodos HTTP, contratos JSON, regras de negócio, autenticação e tratamento de respostas da API.

---

## 2. Escopo

Serão testados os principais endpoints da API Restful Booker, abrangendo operações de autenticação e gerenciamento de reservas.

### Endpoints contemplados

* POST /auth
* GET /booking
* GET /booking/{id}
* POST /booking
* PUT /booking/{id}
* DELETE /booking/{id}

---

## 3. Objetivos dos Testes

Verificar se os endpoints respondem conforme especificado na documentação da API.

Validar:

* Métodos HTTP suportados
* Códigos de resposta HTTP
* Estrutura e contratos JSON
* Regras de negócio
* Processo de autenticação
* Integridade dos dados retornados
* Tratamento de requisições inválidas

---

## 4. Tipos de Teste

### Testes Funcionais

Validação do comportamento esperado dos endpoints da API.

### Testes Positivos

Execução de cenários com dados válidos para verificar o funcionamento correto da aplicação.

### Testes Negativos

Execução de cenários com dados inválidos, incompletos ou inexistentes para validar o tratamento de erros.

### Validação de Contrato

Verificação da estrutura dos objetos JSON retornados pela API.

---

## 5. Ambiente de Testes

### API

Restful Booker

URL Base:

https://restful-booker.herokuapp.com

### Ferramentas

* Postman
* Swagger
* Git
* GitHub

---

## 6. Critérios de Entrada

Os testes poderão ser iniciados quando:

* A API estiver disponível para acesso.
* A documentação Swagger estiver acessível.
* O ambiente Postman estiver configurado.
* Os casos de teste estiverem documentados.

---

## 7. Critérios de Saída

Os testes serão considerados concluídos quando:

* Todos os casos de teste planejados forem executados.
* As evidências de execução forem registradas.
* Os defeitos identificados forem documentados.
* Os resultados forem consolidados no repositório do projeto.

---

## 8. Riscos

* Instabilidade temporária da API pública.
* Alterações não documentadas na API.
* Indisponibilidade do ambiente externo.
* Limitações inerentes a uma API pública de demonstração.

---

## 9. Entregáveis

Ao final do projeto serão disponibilizados:

* Plano de Testes
* Cenários de Teste
* Casos de Teste
* Collection Postman
* Environment Postman
* Evidências de Teste
* Registro de Defeitos
* Documentação do Projeto no GitHub

---

## 10. Resultado Esperado

Garantir que os endpoints da API Restful Booker atendam aos requisitos documentados, respondendo corretamente às requisições realizadas e retornando dados consistentes de acordo com as regras de negócio estabelecidas pela aplicação.
