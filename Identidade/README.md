# 🆔 Gestão de Identidade e Acesso (IAM)

> |"A Identidade é o novo perímetro de segurança."|
> |Nesta seção, documento a implementação de controles no **Microsoft Entra ID** para garantir que apenas as pessoas certas tenham o acesso certo, no momento certo.|

---

## # 🔐 Azure Security Lab – Identity Protection & Access Control (AZ-500)

Este repositório demonstra a implementação de controles de segurança de identidade no Azure, alinhados com as melhores práticas da certificação **AZ-500 (Microsoft Azure Security Technologies)**.

O foco está na proteção de identidades e no controle de acesso utilizando:

* Multi-Factor Authentication (MFA)
* Conditional Access
* Privileged Identity Management (PIM)
* Identity Protection

---

## 🎯 Objetivo

Implementar um modelo de segurança baseado em:

* **Zero Trust**
* **Menor privilégio**
* **Acesso Just-in-Time**
* **Detecção e resposta a riscos**

---

## 🔐 1. Multi-Factor Authentication (MFA)

O MFA adiciona uma camada extra de segurança exigindo dois ou mais fatores de autenticação:

### ✔️ Fatores:

* Algo que você sabe (senha)
* Algo que você tem (celular/app)
* Algo que você é (biometria)

### 📌 Implementação:

* Integrado ao Azure AD (Entra ID)
* Aplicado via:

  * Conditional Access (recomendado)
  * Security Defaults

### 🛡️ Benefícios:

* Reduz risco de credenciais comprometidas
* Protege acessos críticos

---

## 🔐 2. Conditional Access (Acesso Condicional)

Permite controlar o acesso com base em regras do tipo:

> **Se (condição), então (ação)**

### ⚙️ Exemplos:

| Condição                  | Ação                   |
| ------------------------- | ---------------------- |
| Login fora do país        | Bloquear acesso        |
| Login de alto risco       | Exigir MFA             |
| Dispositivo não confiável | Bloquear ou restringir |
| Acesso ao portal Azure    | Exigir MFA             |

### 🧩 Componentes:

* Usuários/Grupos
* Aplicações
* Condições (localização, risco, dispositivo)
* Controles (permitir, bloquear, MFA)

---

## 🔐 3. Privileged Identity Management (PIM)

Gerencia acessos privilegiados com o conceito de:

> **Just-in-Time (JIT)** — acesso temporário sob demanda

### ⚙️ Funcionamento:

* Usuário fica como **Elegível**
* Solicita ativação quando necessário
* Pode exigir:

  * MFA
  * Justificativa
  * Aprovação
* Acesso expira automaticamente (ex: 4h)

### 🛡️ Benefícios:

* Elimina privilégios permanentes
* Reduz superfície de ataque
* Garante auditoria completa

---

## 🔐 4. Identity Protection

Detecta automaticamente riscos de identidade usando inteligência da Microsoft.

### 🚨 Tipos de risco:

#### 👤 User Risk

* Conta potencialmente comprometida
* Credenciais vazadas

#### 🔐 Sign-in Risk

* Login suspeito
* Impossible travel
* IP malicioso

### ⚙️ Ações automáticas:

| Condição             | Ação            |
| -------------------- | --------------- |
| Risco de login alto  | Exigir MFA      |
| Usuário comprometido | Reset de senha  |
| Risco crítico        | Bloquear acesso |

---

## 🔗 Integração entre os serviços

Esses recursos trabalham juntos:

* **Conditional Access** aplica políticas
* **MFA** valida identidade
* **PIM** controla privilégios
* **Identity Protection** detecta riscos

---

## 🔍 Boas práticas (AZ-500)

* Usar **Conditional Access + MFA**
* Habilitar políticas baseadas em risco
* Implementar **PIM para roles administrativas**
* Evitar permissões permanentes
* Monitorar logs de autenticação
* Testar políticas com grupo piloto

---

## 🚨 Cenários comuns de prova

* ✔️ Exigir MFA → Conditional Access
* ✔️ Reduzir privilégios → PIM
* ✔️ Detectar login suspeito → Identity Protection
* ✔️ Bloquear acesso por localização → Conditional Access

---

## 📊 Fluxo de segurança implementado

1. Usuário tenta login
2. Identity Protection avalia risco
3. Conditional Access aplica política
4. MFA pode ser exigido
5. Se necessário, acesso privilegiado via PIM (temporário)

---

## 🚀 Conclusão

A combinação de **MFA + Conditional Access + PIM + Identity Protection** implementa um modelo robusto de segurança baseado em identidade, alinhado com o princípio de **Zero Trust** e com os requisitos da certificação AZ-500.

---

## 📁 Próximos passos

* Adicionar prints das configurações
* Criar diagramas de fluxo
* Simular ataques e respostas
* Monitorar logs no Azure

---


*Atualizado em: Abril/2026 - Foco em AZ-500 & Operações de SOC.*
