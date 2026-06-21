# Testes de API REST com Postman — Restful Booker

Projeto desenvolvido com foco em Qualidade de Software (QA), contemplando planejamento, execução e documentação de testes em APIs REST utilizando Postman.

O objetivo é demonstrar um fluxo completo de testes, incluindo validações funcionais, testes negativos, validação de contratos JSON, registro de evidências e documentação de defeitos encontrados durante a execução.

---

# Objetivos

* Validar endpoints REST utilizando Postman.
* Executar testes positivos e negativos.
* Validar códigos de resposta HTTP.
* Validar contratos JSON.
* Registrar evidências dos testes executados.
* Documentar defeitos encontrados.
* Demonstrar boas práticas de QA em APIs.

---

# Tecnologias Utilizadas

* Postman
* REST API
* JSON
* Swagger/OpenAPI
* Git
* GitHub
* Markdown

---

# API Utilizada

Restful Booker

https://restful-booker.herokuapp.com

API pública utilizada para estudos e práticas de testes de software.

---

# Estrutura do Projeto

```text
QA-api-tests-postman/
│
├── collections/
│   └── RestfulBooker.postman_collection.json
│
├── environments/
│   └── Ambiente-RestfulBooker.postman_environment.json
│
├── docs/
│   ├── Planejamento_de_Testes.md
│   ├── Casos_de_Teste.md
│   ├── Relatorio_Execucao.md
│   ├── Registro_de_Defeitos.md
│   │
│   ├── Evidencias/
│   │
│   └── Defeitos/
│       ├── BUG001_API_aceita_data_invalida.md
│       ├── BUG002_API_retorna_500.md
│       └── Evidencias/
│
└── README.md
```

---

# Casos de Teste

## Autenticação

* CT001 - Gerar Token de Acesso
* CT002 - Gerar Token com Credenciais Inválidas

## Reservas

* CT003 - Listar Todas as Reservas
* CT004 - Criar Reserva com Dados Válidos
* CT005 - Consultar Reserva Existente
* CT006 - Consultar Reserva Inexistente
* CT007 - Criar Reserva com Campos Obrigatórios Ausentes
* CT008 - Criar Reserva com Formato de Data Inválido
* CT009 - Atualizar Reserva Existente com Token
* CT010 - Atualizar Reserva Existente sem Token
* CT011 - Atualizar Reserva Inexistente
* CT012 - Excluir Reserva Existente com Token
* CT013 - Excluir Reserva Existente sem Token
* CT014 - Excluir Reserva Inexistente

## Validações Gerais

* CT015 - Validar Contrato JSON da Criação
* CT016 - Validar Contrato JSON da Consulta
* CT017 - Validar Códigos HTTP
* CT018 - Validar Tratamento de Erros

# Resultado da Execução

| Métrica | Resultado |
|----------|----------|
| Casos Planejados | 18 |
| Casos Executados | 18 |
| Casos Aprovados | 16 |
| Defeitos Registrados | 2 |
| Taxa de Execução | 100% |

---

# Postman Flows

Foram criados fluxos visuais para demonstrar a execução dos principais cenários da API.

## Flow 01 - CRUD Positivo

- Autenticação
- Listagem de Reservas
- Criação de Reserva
- Consulta por ID
- Atualização
- Exclusão

## Flow 02 - Validação de Entrada

- Credenciais Inválidas
- Reserva Inexistente
- Campos Obrigatórios Ausentes
- Data Inválida

### Defeitos Identificados

- BUG001 - API aceita criação de reserva com formato de data inválido.
- BUG002 - API retorna HTTP 500 para campos obrigatórios ausentes.

## Flow 03 - Autorização e Recursos

- Atualização sem Token
- Exclusão sem Token
- Atualização de Recurso Inexistente
- Exclusão de Recurso Inexistente

## Flow 04 - Validações Gerais

- Contratos JSON
- Códigos HTTP
- Tratamento de Erros

---

# Defeitos Encontrados

| ID     | Caso de Teste | Descrição                                                  |
| ------ | ------------- | ---------------------------------------------------------- |
| BUG001 | CT008         | API aceita criação de reserva com formato de data inválido |
| BUG002 | CT007         | API retorna HTTP 500 para campos obrigatórios ausentes     |

---

# Resultados

* 18 casos de teste planejados.
* Fluxos positivos e negativos executados.
* Validação de contratos JSON realizada.
* Defeitos identificados e documentados.
* Evidências registradas para rastreabilidade.

---

# Competências Demonstradas

- Plano de Testes
- Cenários de Teste
- Casos de Teste
- Testes Funcionais
- Testes de API REST
- Testes Positivos e Negativos
- Validação de Contratos JSON
- Validação de Códigos HTTP
- Registro de Evidências
- Gestão de Defeitos
- Documentação Técnica
- Postman Flows
- Git e GitHub

---

# Próximas Evoluções

- Execução automatizada com Newman
- Relatórios HTML
- Integração com GitHub Actions
- Pipeline CI/CD para execução automática dos testes

---

# Autor

Victor Hugo

Analista de Testes (QA)

GitHub: https://github.com/CafeteriaDaYuumi

## Versão

v0.3.0-beta

Última atualização: Junho/2026

