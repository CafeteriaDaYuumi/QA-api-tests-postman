# Testes de API REST com Postman - Restful Booker

Projeto desenvolvido com foco em Planejamento, Execução e Documentação de Testes de API REST utilizando Postman.

O objetivo do projeto é validar os principais endpoints da API Restful Booker através de cenários positivos e negativos, verificando códigos HTTP, contratos JSON, autenticação, regras de negócio e tratamento de erros.

---

# Objetivos

* Planejar e documentar os testes da API.
* Validar endpoints REST.
* Verificar códigos de resposta HTTP.
* Validar contratos JSON.
* Executar cenários positivos e negativos.
* Identificar e registrar defeitos.
* Produzir evidências e documentação de testes.
* Demonstrar um fluxo completo de QA Manual.

---

# Tecnologias Utilizadas

* Postman
* REST API
* JSON
* HTTP
* Git
* GitHub

---

# API Utilizada

Restful Booker

```text
https://restful-booker.herokuapp.com
```

API pública utilizada para estudos e prática de testes de software.

---

# Escopo dos Testes

## Autenticação

* Geração de Token
* Validação de Credenciais Inválidas

## Reservas

* Listagem de Reservas
* Consulta por ID
* Criação de Reserva
* Atualização de Reserva
* Exclusão de Reserva

## Validações

* Códigos HTTP
* Contratos JSON
* Tratamento de Erros
* Campos Obrigatórios
* Validação de Dados

---

# Casos de Teste Executados

| ID    | Caso de Teste                                         | Status               |
| ----- | ----------------------------------------------------- | -------------------- |
| CT001 | Gerar Token de Acesso                                 | Aprovado             |
| CT002 | Gerar Token com Credenciais Inválidas                 | Aprovado             |
| CT003 | Listar Todas as Reservas Cadastradas                  | Aprovado             |
| CT004 | Criar Reserva com Dados Válidos                       | Aprovado             |
| CT005 | Consultar Reserva Existente por ID                    | Aprovado             |
| CT006 | Consultar Reserva Inexistente por ID                  | Aprovado             |
| CT007 | Criar Reserva com Campos Obrigatórios Ausentes        | Defeito Identificado |
| CT008 | Criar Reserva com Formato de Data Inválido            | Defeito Identificado |
| CT009 | Atualizar Reserva Existente com Token Válido          | Aprovado             |
| CT010 | Atualizar Reserva Existente sem Token                 | Aprovado             |
| CT011 | Atualizar Reserva Inexistente                         | Aprovado             |
| CT012 | Excluir Reserva Existente com Token Válido            | Aprovado             |
| CT013 | Excluir Reserva Existente sem Token                   | Aprovado             |
| CT014 | Excluir Reserva Inexistente                           | Aprovado             |
| CT015 | Validar Contrato JSON da Criação de Reserva           | Aprovado             |
| CT016 | Validar Contrato JSON da Consulta de Reserva          | Aprovado             |
| CT017 | Validar Código HTTP para Requisições Bem-Sucedidas    | Aprovado             |
| CT018 | Validar Tratamento de Erro para Requisições Inválidas | Aprovado             |

---

# Resultado da Execução

| Métrica                | Resultado |
| ---------------------- | --------- |
| Casos Planejados       | 18        |
| Casos Executados       | 18        |
| Aprovados              | 16        |
| Defeitos Identificados | 2         |
| Taxa de Execução       | 100%      |

---

# Defeitos Identificados

## BUG001

API aceita criação de reserva com formato de data inválido.

**Caso Relacionado:** CT008

**Severidade:** Média

---

## BUG002

API retorna HTTP 500 ao receber campos obrigatórios ausentes.

**Caso Relacionado:** CT007

**Severidade:** Baixa

---

# Estrutura do Projeto

```text
QA-api-tests-postman-sql/
│
├── collections/
├── environments/
│
├── docs/
│   ├── Plano_de_Testes.md
│   ├── Cenarios_de_Teste.md
│   ├── Casos_de_Teste.md
│   ├── Relatorio_de_Execucao.md
│   ├── Registro_de_Defeitos.md
│   │
│   ├── Evidencias/
│   │   ├── CT001
│   │   ├── CT002
│   │   └── ...
│   │
│   └── Defeitos/
│       ├── BUG001_API_aceita_data_invalida.md
│       ├── BUG002_API_retorna_500_para_campos_ausentes.md
│       └── Evidencias/
│
└── README.md
```

---

# Documentação

O projeto contém:

* Plano de Testes
* Cenários de Teste
* Casos de Teste
* Evidências de Execução
* Relatório de Execução
* Registro de Defeitos
* Evidências dos Defeitos

---

# Próximas Evoluções

* Automação da Collection utilizando Newman
* Geração de Relatórios HTML
* Integração com GitHub Actions
* Execução automatizada em Pipeline CI/CD

---

# Autor

Victor Hugo

Analista de Testes (QA) Jr | Testes Manuais | Testes de API | Postman | Jira | Git | SQL
