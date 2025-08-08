# resumelabGerenciandoPoliticasAzure

# 🔐 Gerenciando Políticas e Acessos no Azure – Governança e Conformidade

Este guia apresenta como **definir, criar, gerenciar e monitorar políticas de acesso** no **Microsoft Azure**, garantindo **governança**, **segurança** e **conformidade** com requisitos corporativos e normas internacionais como **ISO 27001, ISO 27017 e ISO 27018**.

---

## 📋 Objetivos
- Garantir que os recursos sigam **padrões de segurança e compliance**.
- Implementar **políticas automatizadas** para controle de criação e configuração de recursos.
- Cumprir **normas ISO, NIST, PCI-DSS, GDPR, LGPD**.
- Controlar acessos via **RBAC**.
- Automatizar **auditorias** e **correções**.

---

## 🏗 Componentes de Governança

### **1. Azure Policy**
Ferramenta para **criar, atribuir e monitorar** regras de conformidade.

**Exemplos de aplicação:**
- Restringir a criação de recursos a regiões específicas.
- Exigir uso de tags obrigatórias.
- Garantir criptografia em discos.

---

### **2. RBAC (Role-Based Access Control)**
Controle de acesso baseado em papéis:
- **Owner:** controle total, incluindo permissões.
- **Contributor:** cria e gerencia recursos, sem mudar permissões.
- **Reader:** acesso somente leitura.

---

### **3. Azure Blueprints**
Permite implantar **ambientes padronizados** com políticas, RBAC e templates ARM.

---

### **4. Monitoramento de Conformidade**
O **Azure Policy Compliance** permite visualizar:
- Recursos conformes e não conformes.
- Percentual de aderência a normas.
- Ações de correção.

---

## 📜 Normas ISO e Conformidade no Azure

O Azure possui certificações de segurança e conformidade que facilitam auditorias e regulamentações.

| Norma ISO       | Descrição                                                                 |
|-----------------|---------------------------------------------------------------------------|
| **ISO 27001**   | Gestão de Segurança da Informação (SGSI).                                 |
| **ISO 27017**   | Controles de segurança para ambientes em nuvem.                           |
| **ISO 27018**   | Proteção de dados pessoais em nuvem pública.                              |
| **ISO 22301**   | Continuidade de negócios e recuperação de desastres.                      |

💡 **Dica:** O Azure disponibiliza **Blueprints** para facilitar a aderência a essas normas.

---

## 🚀 Criando Políticas no Azure Policy

### **1️⃣ Criar uma Política Personalizada**
1. Acesse o **Portal do Azure** → **Azure Policy**.
2. Clique em **Definições** → **+ Definição de Política**.
3. Preencha:
   - **Nome da política**.
   - **Descrição** clara.
   - **Categoria** (Governança, Segurança, etc.).
4. No campo **Definição de Política (JSON)**, insira a regra desejada.
5. Salve a política.

---

### **2️⃣ Atribuir a Política**
1. Na lista de políticas, selecione a que você criou.
2. Clique em **Atribuir**.
3. Defina o **escopo** (assinatura, grupo de recursos ou recurso específico).
4. Configure **parâmetros** (ex.: lista de regiões permitidas).
5. Salve.

---

### **3️⃣ Exemplo de Política JSON – Restringir Regiões**
```json
{
  "properties": {
    "displayName": "Allowed locations",
    "policyType": "Custom",
    "mode": "All",
    "parameters": {
      "listOfAllowedLocations": {
        "type": "Array",
        "metadata": {
          "description": "Allowed Azure locations",
          "displayName": "Allowed locations"
        }
      }
    },
    "policyRule": {
      "if": {
        "not": {
          "field": "location",
          "in": "[parameters('listOfAllowedLocations')]"
        }
      },
      "then": {
        "effect": "Deny"
      }
    }
  }
}
4️⃣ Monitorar Conformidade
Vá em Azure Policy → Conformidade.

Veja quais recursos estão fora do padrão.

Execute Correção automática (quando aplicável).

💡 Boas Práticas
Princípio do Menor Privilégio: no RBAC, dê apenas o acesso necessário.

Use tags obrigatórias para rastreamento e cobrança.

Habilite auditorias no Azure Policy e Defender for Cloud.

Revise políticas e permissões periodicamente.

Use Blueprints prontos para normas ISO/NIST.

