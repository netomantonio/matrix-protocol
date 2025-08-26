# MOC — Matrix Ontology Catalog
**Acrônimo:** MOC  
**Status:** Ativo  
**Versão:** 1.0.0  
**Data:** 2025-01-25  

> ⚠️ **IMPORTANTE**: Este documento é uma tradução informativa. A versão autoritativa é [MOC_MATRIX_ONTOLOGY_CATALOG.md](MOC_MATRIX_ONTOLOGY_CATALOG.md).

> 🚨 **AVISO IMPORTANTE**: Este documento contém EXEMPLOS ILUSTRATIVOS (como `technical`, `business`, `draft`, etc.) que NÃO são taxonomias obrigatórias. Cada organização define suas próprias hierarquias conforme suas necessidades específicas. Exemplos servem apenas como referência conceitual.

> "A flexibilidade local preserva a coerência global."

---

## 1. Introdução

O **Matrix Ontology Catalog (MOC)** é o componente fundamental que permite ao Protocolo Matrix separar conceitos centrais universais de taxonomias e estruturas organizacionais específicas.

O MOC define **hierarquias configuráveis** para qualquer conceito que dependa de estruturas organizacionais, mantendo consistência conceitual global enquanto permite adaptabilidade local total.

O MOC atua como o sistema de governança e configuração que permite diferentes organizações adaptarem o Protocolo Matrix às suas estruturas específicas sem perder a interoperabilidade conceitual.

---

## 2. Termos e Definições

- **Conceitos Centrais**: Elementos universais fixos do protocolo (scope, domain, maturity)
- **Taxonomias Locais**: Estruturas hierárquicas específicas definidas por cada organização
- **Hierarquias Configuráveis**: Sistemas de classificação adaptáveis às necessidades organizacionais
- **Nós MOC**: Elementos individuais dentro de uma hierarquia (ex: "team", "technical", "draft")
- **Governança Organizacional**: Regras de autoridade, visibilidade e propagação específicas

Referências adicionais no **MOC organizacional** para definições ontológicas específicas.

---

## 3. Conceitos Centrais

### Separação Conceitual Fundamental

**Conceitos Centrais (Universais)**
- Fixos e imutáveis em todas as implementações
- Exemplos: escopo, domínio, maturidade, propagação, checkpoints de fluxo
- Definidos pelo Protocolo Matrix

**Taxonomias Locais (Configuráveis)**
- Definidas pelo implementador no MOC
- Exemplos: nomes específicos de escopos, estrutura de domínios, papéis organizacionais
- Adaptáveis ao contexto organizacional

### Hierarquias Semânticas Configuráveis

Todo conceito hierárquico deve:
- Ser definido conceitualmente pelo protocolo
- Ter sua hierarquia concreta fornecida pelo MOC
- Permitir reorganização sem quebrar MEF, ZOF ou OIF
- Manter relacionamentos semânticos estáveis

### Princípio da Flexibilidade Local
O MOC garante que estruturas organizacionais específicas não conflitem com a interoperabilidade conceitual do protocolo, permitindo adaptação total mantendo coerência global.

---

## 4. Regras Normativas

> ⚠️ Esta seção é **normativa**.

### Estrutura Obrigatória do MOC
Todo MOC organizacional DEVE conter:
1. **Metadados de versão**: versão, organização, datas de criação/modificação
2. **Hierarquias mínimas**: scope, domain, maturity, evaluation_criteria
3. **Regras de governança**: controle de versão, auditoria, resolução de conflitos
4. **Nós com metadados completos**: id, label, parent, level, governance

### Hierarquias Obrigatórias
- **scope**: DEVE definir alcance e visibilidade do conhecimento
- **domain**: DEVE definir áreas de conhecimento e especialização  
- **maturity**: DEVE definir níveis de validação e confiabilidade
- **evaluation_criteria**: DEVE definir critérios para checkpoint EvaluateForEnrich

### Regras de Integridade
- Nós DEVEM ter identificadores únicos dentro de cada hierarquia
- Relacionamentos parent-child DEVEM ser consistentes
- Níveis hierárquicos DEVEM ser sequenciais (0, 1, 2...)
- Regras de governança DEVEM ser definidas para todos os nós

### Controle de Mudanças
- Alterações no MOC DEVEM ser versionadas
- Impacto em UKIs dependentes DEVE ser analisado
- Aprovação por autoridade competente DEVE ser obrigatória
- Notificações automáticas DEVEM ser enviadas para afetados

### 🔐 Serviço de Validação de Autoridade (Normativo)

O **MOC (Matrix Ontology Catalog)** é a referência canônica para **validação de autoridade** no Protocolo Matrix.  
Esse serviço não executa decisões ou orquestrações (papel do ZOF/OIF), mas define as **regras e ontologia** necessárias para validar se um usuário PODE realizar determinada operação.

#### Interface do Serviço
- **Parâmetros de entrada**:  
  - `user_moc_context` (contexto hierárquico: escopo, domínio, níveis de autoridade)  
  - `operation` (read, enrich, promote, create, update, delete)  
  - `scope_ref` (escopo do conhecimento alvo)  
  - `domain_ref` (domínio do conhecimento alvo)  
  - `type_ref` (tipo do conhecimento alvo: rule, procedure, policy, etc.)  
  - `maturity_ref` (nível de maturidade do conhecimento alvo)  

- **Saída**:  
  - `authorized: true|false` (resultado da autorização)  
  - `required_authority` (nó ou nível esperado para autorização)  
  - `escalation_hint` (possível nó de autoridade superior para delegação/override)  
  - `moc_nodes_cited` (nós específicos do MOC usados na decisão de validação)

#### Requisitos de Integração com Frameworks
- O **ZOF** DEVE consumir este serviço antes do enriquecimento (checkpoint EvaluateForEnrich)  
- O **OIF** DEVE explicar decisões de validação aos usuários, citando nós relevantes do MOC  
- O **MEF** DEVE validar autoridade de criação de UKI via este serviço antes de persistir conhecimento

---

## 5. Interoperabilidade

- **MEF (Matrix Embedding Framework)**: Utiliza referências MOC em campos scope_ref, domain_ref, maturity_ref
- **ZOF (Zion Orchestration Framework)**: Consulta MOC no checkpoint EvaluateForEnrich para aplicar critérios organizacionais
- **OIF (Operator Intelligence Framework)**: Aplica filtragem e controle de acesso baseado em hierarquias MOC
- **MEP (Matrix Epistemic Principle)**: Fornece base para autoridade derivada via estruturas organizacionais MOC

---

## 6. Convenções e Exemplos

Todos os exemplos neste documento são **meramente ilustrativos** e não definem comportamento normativo.  
A semântica normativa (escopos, governança, arquétipos, critérios de enriquecimento) é sempre derivada do **MOC (Matrix Ontology Catalog)** de cada organização.  
Os exemplos são fornecidos para fins de clareza e PODEM ser adaptados aos contextos locais, mas NÃO DEVEM ser tratados como obrigações no nível do protocolo.

---

## 7. Exemplos Ilustrativos (Apêndice)

> **Exemplo (Informativo, Dependente do MOC organizacional)**

### **Estrutura Base do MOC**
```yaml
# --- Exemplo Ilustrativo ---
moc_version: "1.0"
organization: "[Nome da Organização]"
created_date: "[YYYY-MM-DD]"
last_modified: "[YYYY-MM-DD]"
version: "[MAJOR.MINOR.PATCH]"

hierarchies:
  scope:
    metadata:
      concept: "Alcance e visibilidade do conhecimento"
    nodes:
      - id: "personal"    # EXEMPLO
        label: "Pessoal"
        level: 0
        governance:
          visibility: ["owner"]
          authority_required: "self"
      - id: "team"        # EXEMPLO
        label: "Equipe"
        level: 1
        governance:
          visibility: ["team_members"]
          authority_required: "team_lead"
```

### **Integração MEF**
```yaml
# --- Exemplo Ilustrativo ---
# Campos MOC no MEF:
scope_ref: "team"           # Referência ao nó MOC
domain_ref: "technical"     # Referência ao nó MOC
maturity_ref: "approved"    # Referência ao nó MOC
```

### **Integração ZOF**
```yaml
# --- Exemplo Ilustrativo ---
# Checkpoint EvaluateForEnrich:
flow_execution:
  - state: "evaluate_for_enrich"
    signals:
      context: "Avaliando se conhecimento gerado deve enriquecer Oracle"
      criteria_refs: ["relevance", "reusability", "impact"]  # Referências MOC
      decision: "Baseado em critérios MOC específicos da organização"
      result: "Aprovado para enriquecimento com escopo 'team'"
```

### **Integração OIF**
```yaml
# --- Exemplo Ilustrativo ---
# Controle de Acesso:
user_context:
  scope_level: "team" 
  domain_access: ["technical", "business"]
  
access_control:
  uki_filtering: "baseado em scope_ref e domain_ref do usuário"
  explanation_refs: "cita nós MOC específicos nas justificativas"
```

### **Governança e Versionamento**
```yaml
# --- Exemplo Ilustrativo ---
governance:
  version_control:
    change_approval_required: true
    change_authority: "architecture_committee"
    impact_analysis_required: true
  
  audit_trail:
    track_changes: true
    change_notifications: ["all_users"]
    validation_frequency_days: 90
```

**Benefícios Ilustrativos:**
- *Flexibilidade*: Organização adapta estruturas às necessidades específicas
- *Governança*: Regras claras e auditáveis para mudanças
- *Evolução*: Mudanças organizacionais não quebram o protocolo
- *Interoperabilidade*: Diferentes organizações podem compartilhar conhecimento
- *Contexto IA*: Inteligências entendem hierarquias organizacionais específicas

---

## 8. Referências Cruzadas

- [MEF — Matrix Embedding Framework](MEF_MATRIX_EMBEDDING_FRAMEWORK.md)  
- [ZOF — Zion Orchestration Framework](ZOF_ZION_ORCHESTRATION_FRAMEWORK.md)  
- [OIF — Operator Intelligence Framework](OIF_OPERATOR_INTELLIGENCE_FRAMEWORK.md)  
- [MEP — Matrix Epistemic Principle](MEP_MATRIX_EPISTEMIC_PRINCIPLE.md)  