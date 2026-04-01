# 🆔 Gestão de Identidade e Acesso (IAM)

> "A Identidade é o novo perímetro de segurança." 🛡️
> Nesta seção, documento a implementação de controles no **Microsoft Entra ID** para garantir que apenas as pessoas certas tenham o acesso certo, no momento certo.

---

## 📚 Tópicos de Estudo (Foco AZ-500)

| Recurso | O que é? | Objetivo de Segurança |
| :--- | :--- | :--- |
| **MFA** | Multi-Factor Authentication | Adicionar uma camada extra de verificação além da senha.
|🔐 Implementação de MFA no Azure (AZ-500)

Este projeto demonstra a implementação de Multi-Factor Authentication (MFA) no ambiente Azure, seguindo as boas práticas recomendadas para a certificação AZ-500.

O MFA adiciona uma camada extra de segurança ao processo de autenticação, exigindo que o usuário forneça dois ou mais fatores de verificação antes de acessar recursos.

🎯 Objetivos

Reduzir riscos de comprometimento de credenciais
Proteger identidades e acessos privilegiados
Atender requisitos de segurança e compliance

⚙️ Métodos de MFA suportados

Microsoft Authenticator (push notification)
Código via SMS
Chamadas telefônicas
Token OATH (hardware/software)

🛠️ Implementação

O MFA pode ser configurado de duas formas principais:

1. Security Defaults
Habilitação rápida para todos os usuários
MFA obrigatório para contas administrativas
Proteção básica recomendada para ambientes pequenos
2. Conditional Access (Recomendado)

Permite aplicar MFA com base em condições como:

Localização (IP / país)
Dispositivo (compliance)
Aplicação acessada
Risco de login (Identity Protection)

Exemplo de política:

Exigir MFA para acesso ao portal do Azure
Exigir MFA para usuários com privilégios elevados
Bloquear acesso de locais não confiáveis

🔍 Boas práticas (AZ-500)

Habilitar MFA para todas as contas administrativas
Preferir Conditional Access ao invés de MFA por usuário
Usar políticas baseadas em risco
Integrar com Identity Protection
Monitorar logs via Azure AD Sign-in logs

| **Conditional Access** | Acesso Condicional | Aplicar políticas "se-então" (ex: Se o IP é estrangeiro, então bloqueie).
|🔐 Conditional Access (Acesso Condicional)

O Conditional Access no Azure é um mecanismo de segurança baseado em políticas que utiliza a lógica “se-então” (if-then) para controlar o acesso a recursos.

👉 Ele permite aplicar controles de segurança dinâmicos com base no contexto do login.

🧠 Como melhorar seu tópico (versão revisada)

Você pode substituir pelo modelo abaixo 👇

🔐 Conditional Access | Acesso Condicional

O Conditional Access é uma funcionalidade do Azure AD (Microsoft Entra ID) que permite aplicar políticas de acesso baseadas em condições específicas, utilizando a lógica:

Se (condição), então (ação de controle)

🎯 Objetivo

Garantir que apenas acessos seguros e confiáveis sejam permitidos, reduzindo riscos de comprometimento de identidade.

⚙️ Exemplos de políticas (modelo AZ-500)

Condição (IF)	Ação (THEN)
Se o usuário estiver fora do Brasil	Bloquear acesso
Se o login for de alto risco	Exigir MFA
Se o dispositivo não for confiável	Bloquear ou exigir conformidade
Se acessar o portal do Azure	Exigir MFA
Se for conta administrativa	Exigir MFA sempre

🔐 Componentes principais

Usuários/Grupos → quem será afetado
Cloud Apps → qual recurso será protegido
Condições → localização, dispositivo, risco, etc
Controles de acesso → permitir, bloquear, exigir MFA

🛡️ Controles mais usados

Exigir MFA
Exigir dispositivo compatível (Intune)
Bloquear acesso
Exigir mudança de senha
Aplicar políticas baseadas em risco

🔍 Boas práticas (AZ-500)

Sempre usar Conditional Access + MFA
Evitar MFA por usuário (legado)
Aplicar políticas para:
Contas administrativas
Acesso ao Azure Portal
Bloquear países suspeitos (geo-blocking)
Usar modo relatório (Report-only) antes de ativar
Testar com grupo piloto

🚨 Exemplo prático (nível prova)

Política: Bloquear acessos internacionais

Se: Localização ≠ Brasil
Então: Bloquear acesso

👉 Esse tipo de política é muito cobrado na AZ-500.

💡 Dica estratégica pra prova

Na dúvida entre opções:

👉 Sempre escolha soluções que envolvam:

Conditional Access
MFA
Identity Protection
| **PIM (Entra ID Governance)** | Privileged Identity Management | Acesso "Just-in-Time" (ADM apenas por 4h, por exemplo). |
| **Identity Protection** | Proteção de Identidade | Detecção automática de usuários de risco e credenciais vazadas. |

---

## 🔍 Visão de Analista de SOC (Blue Team)

No meu dia a dia no **SOC**, utilizo esses conceitos para investigar incidentes e endurecer as defesas:

### 🚩 Cenários de Investigação
- **Logins Improváveis:** Analisar o `SigninLogs` para identificar acessos de localizações geográficas atípicas.
- **Escalação de Privilégio:** Monitorar logs de auditoria do **PIM** para garantir que ninguém ativou uma role de Global Admin sem justificativa.
- **MFA Fatigue:** Investigar múltiplos pedidos de MFA negados, o que pode indicar um ataque de "fadiga de aprovação".

### ✅ Checklist de Hardening (Identity)
- [ ] Bloquear protocolos de autenticação legada (Legacy Auth).
- [ ] Exigir dispositivos gerenciados (Compliance) para acesso a dados sensíveis.
- [ ] Revisão periódica de usuários convidados (Guest Accounts).
- [ ] Implementação de senhas banidas e proteção de bloqueio inteligente.

---

## 🛠️ Laboratórios Práticos
*Aqui vou listar as evidências (prints ou logs) das minhas configurações:*
1. **Lab 01:** [Configuração de Política de Acesso Condicional para Bloqueio Geográfico]
2. **Lab 02:** [Ativação de Role via PIM com aprovação de terceiros]

---
*Atualizado em: Abril/2026 - Foco em AZ-500 & Operações de SOC.*
