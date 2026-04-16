# aulamax1504# 🏋️ FitPass Gym Management

Sistema de gerenciamento de academias desenvolvido para centralizar o controle de alunos, planos, pagamentos, aulas e acesso físico à unidade.

---


## Sobre o Projeto

O **FitPass** é um sistema de gestão acadêmica voltado para academias de médio e grande porte. Ele integra controle de acesso por RFID, agendamento de aulas, gestão financeira e relatórios gerenciais em uma única plataforma.

---

## Requisitos Funcionais

| ID | Nome | Descrição |
|----|------|-----------|
| **RF01** | Cadastro de Alunos | Permite cadastrar alunos com dados pessoais, contato, endereço e plano contratado |
| **RF02** | Gerenciamento de Planos | Permite criar, editar, ativar e desativar planos (mensal, trimestral, anual etc.) |
| **RF03** | Controle de Pagamentos | Registra pagamentos presenciais (dinheiro, cartão, PIX) e gera boletos/cartões online |
| **RF04** | Regularidade do Aluno | Verifica automaticamente se a mensalidade do aluno está em dia |
| **RF05** | Controle de Acesso | Integra à catraca para validar a entrada do aluno por RFID |
| **RF06** | Agendamento de Aulas | Permite ao aluno visualizar horários e reservar vagas em aulas |
| **RF07** | Lista de Presença | Instrutores registram a presença dos alunos nas aulas |
| **RF08** | Avaliação Física | Instrutores registram peso, IMC, percentual de gordura e anexam arquivos |
| **RF09** | Relatórios Gerenciais | Gerente emite relatórios de inadimplência, alunos ativos, acessos e ocupação |
| **RF10** | Notificações | Sistema envia notificações sobre vencimento, agendamento e nova avaliação |

---

## Diagrama de Casos de Uso

```
Atores            Casos de Uso
──────────────────────────────────────────────────────
Aluno          →  Visualizar horários de aula
               →  Agendar aula
               →  Realizar pagamento online

Instrutor      →  Registrar presença
               →  Registrar avaliação física

Gerente        →  Gerenciar planos
               →  Emitir relatórios gerenciais

Recepcionista  →  Cadastrar aluno
               →  Registrar pagamento presencial

Sist. Acesso   →  Validar acesso do aluno

               ⟵ «include» ⟶  Verificar regularidade do aluno
               ⟵ «extend»  ⟶  Enviar notificação
```

---


## Atores do Sistema

| Ator | Responsabilidades |
|------|-------------------|
| **Aluno** | Visualizar aulas, agendar, realizar pagamento online |
| **Instrutor** | Registrar presença e avaliações físicas |
| **Gerente** | Gerenciar planos e emitir relatórios |
| **Recepcionista** | Cadastrar alunos e registrar pagamentos presenciais |
| **Sistema de Controle de Acesso** | Validar entrada por RFID na catraca |

---
