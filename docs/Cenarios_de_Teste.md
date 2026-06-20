# Cenários de Teste

## Projeto

Testes de API REST com Postman — Restful Booker

## Objetivo

Este documento apresenta os cenários de teste planejados para validação funcional da API Restful Booker, contemplando autenticação, operações CRUD de reservas, validação de contratos JSON, códigos HTTP e tratamento de erros.

---

## Cenários

| ID    | Cenário                                                 | Endpoint      | Método                    | Tipo      |
| ----- | ------------------------------------------------------- | ------------- | ------------------------- | --------- |
| CT001 | Gerar token de autenticação com credenciais válidas     | /auth         | POST                      | Positivo  |
| CT002 | Gerar token de autenticação com credenciais inválidas   | /auth         | POST                      | Negativo  |
| CT003 | Listar todas as reservas cadastradas                    | /booking      | GET                       | Positivo  |
| CT004 | Criar reserva com dados válidos                         | /booking      | POST                      | Positivo  |
| CT005 | Consultar reserva existente por ID                      | /booking/{id} | GET                       | Positivo  |
| CT006 | Consultar reserva inexistente por ID                    | /booking/{id} | GET                       | Negativo  |
| CT007 | Criar reserva com campos obrigatórios ausentes          | /booking      | POST                      | Negativo  |
| CT008 | Criar reserva com formato de data inválido              | /booking      | POST                      | Negativo  |
| CT009 | Atualizar reserva existente com token válido            | /booking/{id} | PUT                       | Positivo  |
| CT010 | Atualizar reserva existente sem token                   | /booking/{id} | PUT                       | Negativo  |
| CT011 | Atualizar reserva inexistente                           | /booking/{id} | PUT                       | Negativo  |
| CT012 | Excluir reserva existente com token válido              | /booking/{id} | DELETE                    | Positivo  |
| CT013 | Excluir reserva existente sem token                     | /booking/{id} | DELETE                    | Negativo  |
| CT014 | Excluir reserva inexistente                             | /booking/{id} | DELETE                    | Negativo  |
| CT015 | Validar contrato JSON da resposta de criação de reserva | /booking      | POST                      | Contrato  |
| CT016 | Validar contrato JSON da consulta de reserva por ID     | /booking/{id} | GET                       | Contrato  |
| CT017 | Validar código HTTP para requisições bem-sucedidas      | Todos         | GET / POST / PUT / DELETE | Funcional |
| CT018 | Validar tratamento de erro para requisições inválidas   | Todos         | GET / POST / PUT / DELETE | Negativo  |

---

## Cobertura dos Testes

### Autenticação

* Geração de token com credenciais válidas.
* Validação de falha de autenticação com credenciais inválidas.

### Consulta de Reservas

* Listagem de reservas cadastradas.
* Consulta de reserva existente.
* Consulta de reserva inexistente.

### Criação de Reservas

* Criação de reserva com dados válidos.
* Criação de reserva com campos obrigatórios ausentes.
* Criação de reserva com formato de data inválido.

### Atualização de Reservas

* Atualização de reserva com autenticação válida.
* Tentativa de atualização sem autenticação.
* Tentativa de atualização de reserva inexistente.

### Exclusão de Reservas

* Exclusão de reserva com autenticação válida.
* Tentativa de exclusão sem autenticação.
* Tentativa de exclusão de reserva inexistente.

### Validações

* Validação de contrato JSON das respostas.
* Validação dos códigos HTTP retornados.
* Validação do tratamento de erros da API.

---

## Observações

Os cenários listados servirão como base para a elaboração dos casos de teste detalhados, incluindo pré-condições, massa de dados, passos de execução e resultados esperados.

A execução dos testes será realizada utilizando o Postman e a documentação oficial da API Restful Booker como referência.

As evidências obtidas durante a execução deverão ser registradas e armazenadas no repositório do projeto.

Qualquer divergência entre o comportamento esperado e o comportamento observado deverá ser documentada no Registro de Defeitos.
