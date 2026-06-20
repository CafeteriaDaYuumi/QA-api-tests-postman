# Cenários de Teste

## Projeto

Testes de API REST com Postman — Restful Booker

## Objetivo

Este documento apresenta os cenários de teste planejados para validação funcional da API Restful Booker, contemplando autenticação, criação, consulta, atualização e exclusão de reservas.

---

## Cenários

| ID    | Cenário                                                 | Endpoint      | Método              | Tipo      |
| ----- | ------------------------------------------------------- | ------------- | ------------------- | --------- |
| CT001 | Gerar token de autenticação com credenciais válidas     | /auth         | POST                | Positivo  |
| CT002 | Gerar token de autenticação com credenciais inválidas   | /auth         | POST                | Negativo  |
| CT003 | Listar todas as reservas cadastradas                    | /booking      | GET                 | Positivo  |
| CT004 | Consultar reserva existente por ID                      | /booking/{id} | GET                 | Positivo  |
| CT005 | Consultar reserva inexistente por ID                    | /booking/{id} | GET                 | Negativo  |
| CT006 | Criar reserva com dados válidos                         | /booking      | POST                | Positivo  |
| CT007 | Criar reserva com campos obrigatórios ausentes          | /booking      | POST                | Negativo  |
| CT008 | Criar reserva com formato de data inválido              | /booking      | POST                | Negativo  |
| CT009 | Atualizar reserva existente com token válido            | /booking/{id} | PUT                 | Positivo  |
| CT010 | Atualizar reserva existente sem token                   | /booking/{id} | PUT                 | Negativo  |
| CT011 | Atualizar reserva inexistente                           | /booking/{id} | PUT                 | Negativo  |
| CT012 | Excluir reserva existente com token válido              | /booking/{id} | DELETE              | Positivo  |
| CT013 | Excluir reserva existente sem token                     | /booking/{id} | DELETE              | Negativo  |
| CT014 | Excluir reserva inexistente                             | /booking/{id} | DELETE              | Negativo  |
| CT015 | Validar contrato JSON da resposta de criação de reserva | /booking      | POST                | Contrato  |
| CT016 | Validar contrato JSON da consulta de reserva por ID     | /booking/{id} | GET                 | Contrato  |
| CT017 | Validar código HTTP para requisição bem-sucedida        | Todos         | GET/POST/PUT/DELETE | Funcional |
| CT018 | Validar tratamento de erro para requisições inválidas   | Todos         | GET/POST/PUT/DELETE | Negativo  |

---

## Observações

Os cenários listados servirão como base para a criação dos casos de teste detalhados, incluindo pré-condições, massa de dados, passos de execução e resultados esperados.

A execução será realizada no Postman, utilizando a documentação Swagger da API Restful Booker como referência.
