# Matriz de Priorização de Requisitos (Método MoSCoW)

| ID | Requisito | M | S | C | W | Justificativa |
| :--- | :--- | :---: | :---: | :---: | :---: | :--- |
| **RF01** | O sistema deverá permitir o cadastro de pacientes (Nome, CPF, Telefone, Data de Nascimento, E-mail). | **X** | | | | Essencial para a identificação única do paciente e início de qualquer atendimento no sistema. |
| **RF02** | O sistema deverá permitir a consulta de pacientes por CPF, Nome ou Telefone. | **X** | | | | Requisito indispensável para localização rápida de cadastros e prevenção de duplicidades. |
| **RF03** | O sistema deverá permitir o cadastro e a manutenção de médicos e suas respectivas especialidades. | **X** | | | | Necessário para estruturar o corpo clínico e vincular os atendimentos às especialidades. |
| **RF04** | O sistema deverá permitir o cadastro e o gerenciamento das agendas de horários dos médicos. | **X** | | | | Requisito fundamental que define a disponibilidade de atendimento da clínica. |
| **RF05** | O sistema deverá permitir a consulta de horários disponíveis por médico, especialidade e data. | **X** | | | | Indispensável para que a recepção/usuário localize vagas disponíveis para agendamento. |
| **RF06** | O sistema deverá permitir a realização e o registro de agendamentos de consultas. | **X** | | | | Funcionalidade central da aplicação; sem ela o sistema não cumpre seu propósito primário. |
| **RF07** | O sistema deverá permitir o registro de confirmação de presença do paciente. | **X** | | | | Essencial para o controle da recepção, gestão da fila de espera presencial e fluxo de atendimento. |
| **RF08** | O sistema deverá permitir o cancelamento e a remarcação de consultas agendadas. | **X** | | | | Crítico para a manutenção da agenda atualizada e liberação de horários vagos. |
| **RF09** | O sistema deverá enviar lembretes automáticos de consulta para o paciente (via WhatsApp/E-mail). | | **X** | | | Requisito importante para redução de faltas (absenteísmo), porém o sistema pode operar manualmente sem ele no MVP. |
| **RF10** | O sistema deverá gerenciar uma lista de espera de pacientes para horários desocupados por cancelamento. | | | **X** | | Recurso desejável para otimização do preenchimento da agenda, mas não impede o funcionamento básico. |
| **RQ01** | **Segurança e Privacidade (LGPD):** O sistema deve criptografar dados sensíveis de saúde e aplicar controle de acesso baseado em perfis (RBAC). | **X** | | | | Requisito legal obrigatório de conformidade com a LGPD para proteção de dados médicos e pessoais. |
| **RQ02** | **Desempenho:** O tempo de resposta para busca de pacientes e horários disponíveis deve ser inferior a 2 segundos. | | **X** | | | Importante para garantir agilidade no atendimento presencial e telefônico, reduzindo filas na recepção. |
| **RQ03** | **Disponibilidade:** O sistema deve manter alta disponibilidade (99,5% de uptime) durante o horário comercial. | **X** | | | | Quedas no sistema paralisam completamente as operações de recepção e agendamento da clínica. |
| **RQ04** | **Usabilidade:** A interface deve ser responsiva e intuitiva para uso rápido em desktops e tablets por recepcionistas. | | **X** | | | Melhora a produtividade operacional da equipe e minimiza o tempo de treinamento dos funcionários. |
| **RQ05** | **Integração:** O sistema deve integrar-se a uma plataforma externa de Telemedicina para consultas online. | | | | **X** | Funcionalidade com alto impacto de inovação, porém definida fora do escopo do lançamento inicial (MVP). |

---
# Parte A - 5 Requisitos Indispensáveis

| Ordem | ID | Requisito | Por que Precisa Permanecer? |
| :---: | :---: | :--- | :--- |
| 1 | **RF01** | O sistema deverá permitir o cadastro de pacientes (Nome, CPF, Telefone, Data de Nascimento, E-mail). | Essencial para a identificação única do paciente e início de qualquer atendimento no sistema. |
| 2 | **RF03** | O sistema deverá permitir o cadastro e a manutenção de médicos e suas respectivas especialidades. | Necessário para estruturar o corpo clínico e vincular os atendimentos às especialidades. |
| 3 | **RF05** | O sistema deverá permitir a consulta de horários disponíveis por médico, especialidade e data. | Indispensável para que a recepção/usuário localize vagas disponíveis para agendamento. |
| 4 | **RF08** | O sistema deverá permitir o cancelamento e a remarcação de consultas agendadas. | Crítico para a manutenção da agenda atualizada e liberação de horários vagos. |
| 5 | **RQ01** | **Segurança e Privacidade (LGPD):** O sistema deve criptografar dados sensíveis de saúde e aplicar controle de acesso baseado em perfis. | Requisito legal obrigatório de conformidade com a LGPD para proteção de dados médicos e pessoais. |

# Parte B - 3 Requisitos para versão Futura

| ID | Requisito | Impacto ao Adiar |
| :---: | :--- | :--- |
| **RF01** | O sistema deverá disponibilizar um painel/dashboard com indicadores de desempenho (quantidade de consultas, faltas, cancelamentos). | OS Médicos terão mais controle de seus atendimentos e os pacientes saberão com qual Médico seria mais fácil de Agendar suas exames |
| **RF03** | O sistema deverá registrar o motivo do cancelamento ou falta (no-show) do paciente. | O paciente saberá o motivo do cancelamento da sua consulta |
| **RF09** | O sistema deverá disparar notificações automáticas aos pacientes afetados caso haja alteração na agenda do médico | O paciente terá maior facilidade de saber seu horário para atendimento |



### Legenda do Método MoSCoW:
* **M (Must Have):** Requisitos essenciais/obrigatórios para o sistema funcionar (MVP).
* **S (Should Have):** Requisitos importantes que agregam alto valor, mas não impedem o lançamento.
* **C (Could Have):** Requisitos desejáveis/confortáveis que serão implementados se houver tempo/recursos.
* **W (Won't Have / Would Have):** Requisitos acordados para não serem incluídos nesta versão/entrega.

### Alunos:
**Lucas Martins Barreto**

**João Pedro Duarte Borges**

**Henrique Mota Monteiro**

**Yuri Marques Oliveira**

**Lucas de Oliveira Andrade**

**Felipe Roosevelt Duarte**
