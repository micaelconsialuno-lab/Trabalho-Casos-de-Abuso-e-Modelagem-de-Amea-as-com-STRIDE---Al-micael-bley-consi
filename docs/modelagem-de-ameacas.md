Modelagem de Ameaças com STRIDE

''Disciplina''
Engenharia de Software Seguro (EAD) 

''Integrantes''
- Micael Bley Consi

''Repositório''
https://github.com/micaelconsialuno-lab/Trabalho-Casos-de-Abuso-e-Modelagem-de-Amea-as-com-STRIDE---Al-micael-bley-cons

1. Identificação do Sistema

Sistema de Agendamento de Consultas Médicas

- Justificativa

O sistema foi escolhido por possuir diferentes tipos de usuários, armazenamento de dados pessoais, autenticação, agendamento de consultas e troca de informações entre pacientes e profissionais da saúde, tornando possível identificar diversas ameaças de segurança.

2. Descrição do Sistema

O sistema permite que pacientes agendem consultas médicas de forma online, podem criar uma conta, realizar login, consultar os horários disponíveis, agendar consultas e cancelar agendamentos, também os profissionais podem visualizar sua agenda e atualizar os horários disponíveis, O administrador gerencia usuários, profissionais e informações do sistema.

As informações armazenadas incluem:
- Dados pessoais
- CPF
- Endereço
- Telefone
- Histórico de consultas
- Login e senha
- Agenda dos médicos

Essas informações precisam ser protegidas contra acessos não autorizados.

---
3. Usuários, Ativos e Pontos de Interação

''Usuários''
- Paciente
- Médico
- Administrador

''Ativos importantes''
- Banco de dados
- Contas dos usuários
- Senhas
- Dados pessoais
- Agenda de consultas
- Histórico médico

''Componentes''
- Aplicativo Web
- Banco de Dados
- API
- Servidor
- Sistema de autenticação

4. Visão Geral da Arquitetura

Fluxo simplificado:
Paciente > Sistema Web > API > Banco de Dados > Médico > Sistema Web > API > Banco de Dados > Administrador > Sistema Web > API > Banco de Dados >

5. Modelagem de Ameaças (STRIDE)

| ID | Categoria | Componente | Ameaça | Impacto |
|----|-----------|------------|--------|---------|
| T01 | Spoofing | Conta do usuário | Utilização de credenciais roubadas | Acesso indevido às informações |
| T02 | Tampering | Banco de Dados | Alteração de consultas | Perda da integridade dos dados |
| T03 | Repudiation | Sistema de Log | Usuário negar alteração realizada | Dificuldade de auditoria |
| T04 | Information Disclosure | Banco de Dados | Vazamento de informações pessoais | Violação da privacidade |
| T05 | Denial of Service | Servidor | Ataques que deixam o sistema indisponível | Interrupção do atendimento |
| T06 | Elevation of Privilege | Sistema | Usuário comum obtém acesso de administrador | Controle indevido do sistema |

6. Casos de Abuso

- CA01 – Acesso utilizando senha roubada

''Ator''

Atacante
 
''Objetivo''

Acessar informações do paciente.

''Condições''

Possuir login e senha da vítima.

''Fluxo''

1. Obtém a senha.
2. Realiza login.
3. Consulta os dados do paciente.
4. Altera informações.

''Impacto''

Exposição de informações pessoais.

**Categorias STRIDE**

- Spoofing
- Information Disclosure

---

## CA02 – Alteração de consultas

**Ator**

Usuário mal-intencionado.

**Objetivo**

Alterar consultas de outros pacientes.

**Condições**

Possuir acesso indevido ao sistema.

**Fluxo**

1. Entra no sistema.
2. Localiza consultas.
3. Altera datas e horários.

**Impacto**

Prejuízo aos pacientes e médicos.

**Categorias**

- Tampering

---

## CA03 – Ataque ao servidor

**Ator**

Atacante externo.

**Objetivo**

Deixar o sistema indisponível.

**Condições**

Enviar grande quantidade de requisições.

**Fluxo**

1. Envia milhares de acessos simultâneos.
2. O servidor fica sobrecarregado.
3. Os usuários não conseguem acessar.

**Impacto**

Indisponibilidade do sistema.

**Categorias**

- Denial of Service

---

# 7. Considerações Finais

A análise permitiu identificar possíveis ameaças relacionadas ao sistema de agendamento de consultas.

Os ativos mais importantes são os dados pessoais dos pacientes, o banco de dados e o sistema de autenticação.

As ameaças com maior impacto são o vazamento de informações, o roubo de credenciais e a indisponibilidade do sistema.

A aplicação do STRIDE auxiliou na identificação das principais vulnerabilidades antes da implementação do software.
