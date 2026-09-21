# Documentação do Trabalho – Engenharia de Requisitos

**Integrantes e Papéis:**
* [Lucas Martins Barreto](https://github.com/LucasBarretoDev-eng) - Documentação
* [João Pedro Duarte Borges](https://github.com/nomedeusuario2) - Analista de Requisitos
* [Felipe Roosevelt](https://github.com/nomedeusuario3) - Analista de Processos
* **Lucas de Oliveira Andrade** = Representante do Cliente
* **Yuri Marques Oliveira** = Representante da Clínica
* **Henrique Mota Monteiro** = Modelador

---

## 1. Análise do Negócio

### 1.1. Identificação do Processo

* **Nome do processo:** Processo de Atendimento e Agendamento de Consultas da Clínica Vida+ Saúde
* **Objetivo do processo:** Garantir que o paciente consiga solicitar, agendar e receber atendimento médico de forma organizada, confiável e sem retrabalho, evitando conflitos de horário e falhas de comunicação.
* **Cliente do processo:** O paciente, é ele quem solicita o serviço e recebe o valor final (a consulta realizada).
* **Quem executa as atividades:** Recepcionistas (cadastro, agendamento, confirmação, cancelamentos) e médicos (realização da consulta e registro do atendimento).
* **Quem gerencia o processo:** A direção/gerência da clínica, que acompanha o desempenho por meio de indicadores.
* **Evento que inicia o processo:** O paciente entra em contato (telefone, WhatsApp ou presencialmente) solicitando um agendamento.
* **Evento que encerra o processo:** O médico registra as informações do atendimento após a consulta ser realizada.
* **Valor entregue ao cliente:** Acesso rápido e confiável a uma consulta médica, com confirmação clara do horário, sem precisar repetir dados já cadastrados e com comunicação eficiente em caso de mudanças.

---

### 1.2. Identificação dos Stakeholders

| Stakeholder | Interesse no processo | Participação | Necessidades |
| :--- | :--- | :--- | :--- |
| **Paciente** | Conseguir agendar e ser atendido de forma rápida, sem burocracia ou erros de agenda | Solicita o agendamento, fornece dados pessoais, comparece à consulta, pode cancelar/remarcar | Agendamento simples, confirmação confiável, lembretes automáticos, não precisar repetir dados a cada contato |
| **Recepcionista** | Realizar agendamentos sem conflitos e sem retrabalho manual | Atende solicitações, consulta a agenda, registra e confirma agendamentos, trata cancelamentos | Sistema centralizado, atualizado em tempo real, fácil e rápido de usar |
| **Médico** | Ter uma agenda organizada, sem conflitos de horário, e tempo adequado para cada atendimento | Define sua disponibilidade, realiza as consultas, registra informações do atendimento | Visibilidade da própria agenda e integração entre o agendamento e o prontuário do paciente |
| **Gerente** | Operação eficiente da clínica, sem gargalos no atendimento | Supervisiona a recepção e a organização das agendas | Dados confiáveis para tomar decisões operacionais no dia a dia |
| **Direção** | Melhorar o desempenho da clínica e reduzir faltas/cancelamentos | Define diretrizes e acompanhar indicadores de desempenho | Dashboard com indicadores, redução de custos e retrabalho operacional |
| **Equipe de TI** | Sistema estável, sustentável e fácil de manter | Implementa e mantém o sistema de agendamento | Implementa e mantém o sistema de agendamento |

---

### 1.3. Análise do Processo Atual

| Pergunta / Dimensão | Resumo do Processo |
| :--- | :--- |
| **Quem utilizará o sistema** | **Cliente:** Paciente.<br>**Executores:** Recepcionistas (agendamentos e cadastros) e Médicos (consultas e prontuários).<br>**Gerenciamento:** Direção da clínica. |
| **Entradas e Saídas** | **Entradas:** Dados do paciente, solicitações, especialidade, disponibilidades e cancelamentos.<br>**Saídas:** Consultas agendadas, atendimentos realizados, registros e indicadores. |
| **Recursos e Ferramentas** | **Recursos:** Pessoas, computadores e canais de contato.<br>**Ferramentas:** Planilhas (agenda), WhatsApp, telefone e sistema médico. |
| **Problemas** | Descentralização de dados, planilhas ou WhatsApp divergentes, trabalho manual e conflitos de horários. |
| **Pontos Positivos** | Múltiplos canais de contato, processo definido e interesse em indicadores. |
| **Indicadores** | Volume de consultas, taxas de faltas e cancelamentos, tempo médio de atendimento e ocupação da agenda. |
| **Quando começa o uso do sistema** | **Início:** Contato inicial do paciente.<br>**Execução:** Do agendamento até a consulta.<br>**Fim:** Consulta realizada e dados registrados. |
| **Onde o sistema agirá** | **Início/Execução:** WhatsApp, telefone ou recepção presencial.<br>**Registros:** Planilhas (agendamento) e sistema próprio (prontuário médico). |
| **Objetivo e Valor** | Organizar consultas e a agenda médica.<br>**Valor:** Acesso à saúde para o paciente; organização e controle de desempenho para a clínica. |
| **Fluxo Atual** | Contato do paciente → Verificação e registro manual em planilha → Confirmação → Consulta → Registro do médico em sistema separado. |
| **Comunicação e Exceções** | Comunicação via WhatsApp/telefone/presencial. Cancelamentos e alterações médicas são tratados manualmente caso a caso pela recepção. |

---

### 1.5. Regras de Negócio

| Código | Regra de Negócio | Origem |
| :---: | :--- | :--- |
| **RN01** | Um paciente deve possuir cadastro válido (com CPF) antes de realizar um agendamento. | Evitar cadastros anônimos e duplicidades de registros. |
| **RN02** | Um médico não pode possuir dois agendamentos no mesmo horário. | Eliminar conflitos de agendamento observados no processo atual. |
| **RN03** | Os agendamentos só podem ser efetuados em horários previamente disponibilizados na agenda do médico. | Garantir o cumprimento da grade de trabalho cadastrada pelo profissional. |
| **RN04** | O cancelamento de uma consulta deve liberar o horário imediatamente na agenda global. | Permitir reagendamentos rápidos e otimizar a taxa de ocupação da clínica. |
| **RN05** | Em caso de alteração na agenda do médico, o sistema deve bloquear o período alterado para novos agendamentos. | Prevenir novos conflitos de horários em momentos de imprevistos médicos. |
| **RN06** | Lembretes automáticos de consulta devem ser enviados ao paciente com 24 horas de antecedência. | Reduzir a taxa de não comparecimento (*no-show*) dos pacientes. |
| **RN07** | Apenas usuários com perfil “Médico” podem registrar ou alterar informações relativas ao atendimento/prontuário pós-consulta. | Garantir sigilo, ética e integridade nos dados de saúde dos pacientes. |
| **RN08** | Todo agendamento deve ter seu status atualizado automaticamente (Agendado, Confirmado, Em Atendimento, Concluído, Cancelado, Falta). | Prover a base de dados necessária para o cálculo de indicadores de desempenho. |
| **RN09** | Caso um paciente cancele com mais de 2 horas de antecedência, o sistema deve sugerir aos pacientes da lista de espera para preencher o horário. | Reduzir o tempo ocioso dos médicos e acelerar o atendimento da demanda reprimida. |
| **RN10** | Não deve ser permitida a exclusão física de cadastros de pacientes com histórico de consultas. | Manter a conformidade legal (LGPD e CFM) e preservar o histórico do paciente. |

---

## 2. Modelagem e Melhorias

### 2.1. Proposta de Melhorias

| Problema | Melhoria proposta | Benefício esperado |
| :--- | :--- | :--- |
| Cadastros duplicados e retrabalho no atendimento por uso de planilhas individuais. | Implantar cadastro único e centralizado com busca obrigatória por CPF antes do registro. | Eliminação de registros duplicados e agilidade na identificação do paciente. |
| Conflitos de horários na agenda do mesmo médico por concorrência entre recepcionistas. | Criar agenda médica centralizada em tempo real com bloqueio transacional de horários. | Fim dos agendamentos em duplo horário e total confiabilidade das agendas. |
| Ausência de mecanismo automático para lembrar pacientes, provocando altos índices de faltas. | Automatizar o envio de lembretes de consulta por WhatsApp e E-mail 24h antes da consulta. | Redução expressiva na taxa de faltas (*no-show*) e melhor aproveitamento da agenda. |
| Gerenciamento manual e demorado de reagendamentos quando ocorrem cancelamentos. | Implementar módulo automatizado de lista de espera com notificação para novos horários vagos. | Preenchimento rápido de lacunas de agenda e redução do tempo ocioso do médico. |
| Contato manual exaustivo da recepção com pacientes ao ocorrer alteração na agenda do médico. | Criar funcionalidade de remanejamento com notificação automática e instantânea aos pacientes afetados. | Redução da carga operacional da recepção e comunicação mais rápida e assertiva. |
| Inexistência de confirmação ativa de agendamentos pelo próprio paciente. | Disponibilizar confirmação bidirecional (link interativo no WhatsApp/E-mail) atualizando o status na hora. | Previsibilidade exata da presença dos pacientes no dia da consulta. |
| Desconexão entre o atendimento médico e a recepção, com prontuário em sistema separado. | Integrar o registro pós-consulta do médico à mesma plataforma centralizada. | Histórico clínico unificado, eliminação de retrabalho e integridade das informações. |
| Falta de visibilidade gerencial sobre desempenho, consultas realizadas, faltas e cancelamentos. | Desenvolver dashboard de indicadores gerenciais em tempo real para a gestão e direção da clínica. | Tomada de decisão baseada em dados e facilidade no acompanhamento de metas institucionais. |

---

### 2.2. Modelagem AS-IS e TO-BE

#### Processo AS-IS
*(Inserir diagrama ou descrição detalhada do fluxo atual aqui)*

#### Processo TO-BE
*(Inserir diagrama ou descrição detalhada do fluxo proposto aqui)*

---

## 3. Engenharia de Requisitos

### 3.1. Requisitos Funcionais

| Código | Requisito Funcional | Prioridade |
| :---: | :--- | :---: |
| **RF01** | O sistema deverá permitir o cadastro de pacientes. | Must Have |
| **RF02** | O sistema deverá permitir a consulta de pacientes por CPF, Nome ou Telefone. | Must Have |
| **RF03** | O sistema deverá permitir o cadastro de médicos e suas respectivas especialidades. | Must Have |
| **RF04** | O sistema deverá permitir o cadastro e o gerenciamento das agendas de horários dos médicos. | Must Have |
| **RF05** | O sistema deverá permitir a consulta de horários disponíveis por médico. | Must Have |
| **RF06** | O sistema deverá permitir a realização e o registro de agendamentos de consultas. | Must Have |
| **RF07** | O sistema deverá permitir o registro de confirmação de presença do paciente. | Must Have |
| **RF08** | O sistema deverá permitir o cancelamento e a remarcação de consultas agendadas. | Must Have |
| **RF09** | O sistema deverá enviar lembretes automáticos de consulta para o paciente (via WhatsApp/E-mail). | Should Have |
| **RF10** | O sistema deverá gerenciar uma lista de espera de pacientes para horários desocupados por cancelamento. | Could Have |
| **RF11** | O sistema deverá disparar notificações automáticas aos pacientes afetados caso haja alteração na agenda do médico. | Could Have |
| **RF12** | O sistema deverá permitir ao médico registrar as informações do atendimento (prontuário pós-consulta). | Must Have |
| **RF13** | O sistema deverá registrar o motivo do cancelamento ou falta (*no-show*) do paciente. | Could Have |
| **RF14** | O sistema deverá disponibilizar um painel/dashboard com indicadores de desempenho (quantidade de consultas, faltas, cancelamentos). | Should Have |
| **RF15** | O sistema deverá calcular e exibir a taxa de ocupação dos horários e o tempo médio de atendimento. | Should Have |

---

### 3.2. Requisitos Não Funcionais

| Código | Categoria | Requisito Não Funcional |
| :---: | :--- | :--- |
| **RNF01** | Desempenho | O sistema deverá apresentar os horários disponíveis de um médico em no máximo 5 segundos após a solicitação do usuário. |
| **RNF02** | Segurança | O sistema deverá autenticar os usuários e controlar acessos por perfis. |
| **RNF03** | Privacidade | O sistema deverá armazenar e tratar os dados pessoais dos pacientes de acordo com as normas da LGPD. |
| **RNF04** | Disponibilidade | O sistema deverá apresentar disponibilidade mínima de 99,5% durante o horário de funcionamento da clínica. |
| **RNF05** | Usabilidade | O sistema deverá ser intuitivo, permitindo que a recepcionista conclua um agendamento em no máximo 4 etapas. |
| **RNF06** | Confiabilidade | O sistema deverá utilizar mecanismos de bloqueio para impedir agendamentos concorrentes simultâneos no mesmo milissegundo. |
| **RNF07** | Compatibilidade | O sistema deverá ser acessível via navegadores web modernos (Chrome, Firefox, Edge, Safari), sem necessidade de instalação de plugins adicionais. |
| **RNF08** | Manutenibilidade | O sistema deverá possuir arquitetura modular com código documentado, a fim de facilitar futuras expansões. |
| **RNF09** | Integração | O sistema deverá integrar-se a uma API de mensageria (WhatsApp/E-mail) para o envio automatizado de lembretes. |
| **RNF10** | Portabilidade | A interface do sistema deverá se adaptar a telas de computadores e tablets. |

---

## 4. Indicadores de Desempenho

| Indicador | Objetivo |
| :--- | :--- |
| **Quantidade de consultas realizadas** | Verificar a quantidade de atendimentos realizados em determinado período. |
| **Taxa de cancelamentos** | Acompanhar a quantidade de consultas canceladas. |
| **Taxa de faltas (*No-show*)** | Verificar quantos pacientes não compareceram às consultas. |
| **Tempo médio de atendimento** | Acompanhar quanto tempo, em média, dura cada atendimento. |
| **Taxa de ocupação dos horários** | Verificar quanto dos horários disponíveis dos médicos estão sendo utilizados. |
