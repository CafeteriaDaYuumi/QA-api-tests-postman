# Relatório de Execução dos Testes

## Projeto

Testes de API REST com Postman — Restful Booker

## Ambiente

* Ferramenta: Postman
* API: Restful Booker
* Base URL: https://restful-booker.herokuapp.com
* Data da execução: 20/06/2026
* Executor: Victor Hugo

---

## Checklist de Execução

| ID    | Caso de Teste                                         | Pré-condição                   | Status                            | Evidência | Defeito |
| ----- | ----------------------------------------------------- | ------------------------------ | --------------------------------- | --------- | ------- |
| CT001 | Gerar Token de Acesso                                 | API disponível                 | Aprovado                          | CT001.png | -       |
| CT002 | Gerar Token com Credenciais Inválidas                 | API disponível                 | Aprovado                          | CT002.png | -       |
| CT003 | Listar Todas as Reservas Cadastradas                  | API disponível                 | Aprovado                          | CT003.png | -       |
| CT004 | Criar Reserva com Dados Válidos                       | API disponível                 | Aprovado                          | CT004.png | -       |
| CT005 | Consultar Reserva Existente por ID                    | Executar CT004                 | Aprovado                          | CT005.png | -       |
| CT006 | Consultar Reserva Inexistente por ID                  | Usar ID inexistente            | Aprovado                          | CT006.png | -       |
| CT007 | Criar Reserva com Campos Obrigatórios Ausentes        | API disponível                 | Aprovado com Defeito Identificado | CT007.png | BUG-002 |
| CT008 | Criar Reserva com Formato de Data Inválido            | API disponível                 | Aprovado com Defeito Identificado | CT008.png | BUG-001 |
| CT009 | Atualizar Reserva Existente com Token Válido          | Executar CT001 e CT004         | Aprovado                          | CT009.png | -       |
| CT010 | Atualizar Reserva Existente sem Token                 | Executar CT004 e remover token | Aprovado                          | CT010.png | -       |
| CT011 | Atualizar Reserva Inexistente                         | Executar CT001                 | Aprovado                          | CT011.png | -       |
| CT012 | Excluir Reserva Existente com Token Válido            | Executar CT001 e CT004         | Aprovado                          | CT012.png | -       |
| CT013 | Excluir Reserva Existente sem Token                   | Executar CT004 e remover token | Aprovado                          | CT013.png | -       |
| CT014 | Excluir Reserva Inexistente                           | Executar CT001                 | Aprovado                          | CT014.png | -       |
| CT015 | Validar Contrato JSON da Criação de Reserva           | Body válido                    | Aprovado                          | CT015.png | -       |
| CT016 | Validar Contrato JSON da Consulta de Reserva          | Executar CT004                 | Aprovado                          | CT016.png | -       |
| CT017 | Validar Código HTTP para Requisições Bem-Sucedidas    | Executar cenários positivos    | Aprovado                          | CT017.png | -       |
| CT018 | Validar Tratamento de Erro para Requisições Inválidas | Executar cenários negativos    | Aprovado                          | CT018.png | -       |

---

## Ordem de Execução Realizada

1. CT001 - Gerar Token de Acesso
2. CT002 - Gerar Token com Credenciais Inválidas
3. CT003 - Listar Todas as Reservas Cadastradas
4. CT004 - Criar Reserva com Dados Válidos
5. CT005 - Consultar Reserva Existente por ID
6. CT006 - Consultar Reserva Inexistente por ID
7. CT007 - Criar Reserva com Campos Obrigatórios Ausentes
8. CT008 - Criar Reserva com Formato de Data Inválido
9. CT009 - Atualizar Reserva Existente com Token Válido
10. CT010 - Atualizar Reserva Existente sem Token
11. CT011 - Atualizar Reserva Inexistente
12. CT012 - Excluir Reserva Existente com Token Válido
13. CT013 - Excluir Reserva Existente sem Token
14. CT014 - Excluir Reserva Inexistente
15. CT015 - Validar Contrato JSON da Criação de Reserva
16. CT016 - Validar Contrato JSON da Consulta de Reserva
17. CT017 - Validar Código HTTP para Requisições Bem-Sucedidas
18. CT018 - Validar Tratamento de Erro para Requisições Inválidas

---

## Defeitos Encontrados

### BUG-001

**Título:** API aceita criação de reserva com formato de data inválido.

**Caso de Teste:** CT008 - Criar Reserva com Formato de Data Inválido

**Resultado Esperado:**
A API deveria rejeitar a requisição retornando HTTP 400 Bad Request ou HTTP 422 Unprocessable Entity.

**Resultado Obtido:**
A API retornou HTTP 200 OK e criou a reserva mesmo contendo uma data inválida.

**Severidade:** Média

**Prioridade:** Média

**Status:** Aberto

---

### BUG-002

**Título:** API retorna erro interno ao receber campos obrigatórios ausentes.

**Caso de Teste:** CT007 - Criar Reserva com Campos Obrigatórios Ausentes

**Resultado Esperado:**
A API deveria retornar HTTP 400 Bad Request ou HTTP 422 Unprocessable Entity.

**Resultado Obtido:**
A API retornou HTTP 500 Internal Server Error.

**Severidade:** Baixa

**Prioridade:** Baixa

**Status:** Aberto

---

## Resumo Final

| Métrica                   | Quantidade |
| ------------------------- | ---------- |
| Casos planejados          | 18         |
| Casos executados          | 18         |
| Aprovados                 | 16         |
| Reprovados                | 0          |
| Bloqueados                | 0          |
| Defeitos registrados      | 2          |
| Taxa de execução          | 100%       |
| Taxa de sucesso funcional | 88,9%      |

---

## Conclusão

A suíte de testes foi executada integralmente, contemplando autenticação, operações CRUD de reservas, validação de contratos JSON, validação de códigos HTTP e tratamento de erros.

Os fluxos principais da API apresentaram comportamento conforme esperado, permitindo a criação, consulta, atualização e exclusão de reservas.

Durante a execução foram identificados dois defeitos relacionados à validação de entrada de dados e tratamento de exceções, os quais foram devidamente registrados para acompanhamento.

O projeto encontra-se concluído na fase de testes manuais e documentação, estando apto para evolução para a fase de automação de testes.

---

## Observações

Todas as evidências da execução foram registradas e armazenadas na pasta `/docs/Evidencias`.

Os defeitos identificados foram documentados em `Registro_de_Defeitos.md` para rastreabilidade e acompanhamento.
