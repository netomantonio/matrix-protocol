# 📊 MOC - MATRIX ONTOLOGY CATALOG

> 🚨 **AVISO IMPORTANTE**: Este documento contém EXEMPLOS ILUSTRATIVOS (como `technical`, `business`, `draft`, etc.) que NÃO são taxonomias obrigatórias. Cada organização define suas próprias hierarquias conforme suas necessidades específicas. Exemplos servem apenas como referência conceitual.

## 🌎 Idioma / Language

- [Português 🇧🇷](#português)
- [English 🇺🇸](#english)

---

<a name="português"></a>
# Português 🇧🇷

> "A flexibilidade local preserva a coerência global."

---

## 🌐 Visão Geral do MOC

O **Matrix Ontology Catalog (MOC)** é o componente fundamental que permite ao Protocolo Matrix separar conceitos centrais universais de taxonomias e estruturas organizacionais específicas.

O MOC define **hierarquias configuráveis** para qualquer conceito que dependa de estruturas organizacionais, mantendo consistência conceitual global enquanto permite adaptabilidade local total.

---

## 📋 Princípios Fundamentais

### 🔧 Separação Conceitual

**Conceitos Centrais (Universais)**
- Fixos e imutáveis em todas as implementações
- Exemplos: escopo, domínio, maturidade, propagação, checkpoints de fluxo
- Definidos pelo Protocolo Matrix

**Taxonomias Locais (Configuráveis)**
- Definidas pelo implementador no MOC
- Exemplos: nomes específicos de escopos, estrutura de domínios, papéis organizacionais
- Adaptáveis ao contexto organizacional

### 🏗️ Hierarquias Semânticas Configuráveis

Todo conceito hierárquico deve:
- Ser definido conceitualmente pelo protocolo
- Ter sua hierarquia concreta fornecida pelo MOC
- Permitir reorganização sem quebrar MEF, ZWF ou OIF
- Manter relacionamentos semânticos estáveis

---

## 🗂️ Estrutura do MOC

### Formato Base

```yaml
csh_version: "1.0"
organization: "[Nome da Organização]"
created_date: "[YYYY-MM-DD]"
last_modified: "[YYYY-MM-DD]"
version: "[MAJOR.MINOR.PATCH]"

hierarchies:
  scope:
    metadata:
      concept: "Alcance e visibilidade do conhecimento"
      governance_rules: |
        [Regras de governança para escopos]
    nodes:
      - id: "personal"
        label: "Pessoal"
        parent: null
        level: 0
        governance:
          visibility: ["owner"]
          propagation: "none"
          authority_required: "self"
      - id: "team"
        label: "Equipe"
        parent: "personal"
        level: 1
        governance:
          visibility: ["team_members"]
          propagation: "restricted"
          authority_required: "team_lead"
      - id: "organization"
        label: "Organizacional"
        parent: "team"
        level: 2
        governance:
          visibility: ["all_members"]
          propagation: "automatic"
          authority_required: "architecture_committee"

  domain:
    metadata:
      concept: "Área de conhecimento e especialização"
      governance_rules: |
        [Regras de classificação e propriedade por domínio]
# 🚨 AVISO: EXEMPLOS NÃO SÃO TAXONOMIA OBRIGATÓRIA
# Os nós mostrados abaixo (technical, business, etc.) são APENAS EXEMPLOS ILUSTRATIVOS.
# 🏛️ Cada organização define seus próprios nós conforme sua realidade específica.
    nodes:
      - id: "technical"    # EXEMPLO - cada organização define seus domínios
        label: "Técnico"
        parent: null
        level: 0
        governance:
          owners: ["engineering"]    # EXEMPLO - definir conforme estrutura organizacional
          reviewers: ["tech_leads", "architects"]
      - id: "business"    # EXEMPLO - cada organização define seus domínios
        label: "Negócio"
        parent: null
        level: 0
        governance:
          owners: ["product_managers", "business_analysts"]
          reviewers: ["stakeholders"]

  maturity:
    metadata:
      concept: "Nível de validação e confiabilidade"
      governance_rules: |
        [Critérios para progressão entre níveis]
    nodes:
      - id: "draft"
        label: "Rascunho"
        parent: null
        level: 0
        governance:
          auto_promotion: false
          validation_required: false
      - id: "review"
        label: "Revisão"
        parent: "draft"
        level: 1
        governance:
          auto_promotion: false
          validation_required: true
          reviewers_required: 2
      - id: "approved"
        label: "Aprovado"
        parent: "review"
        level: 2
        governance:
          auto_promotion: false
          validation_required: true
          authority_required: "domain_owner"

  evaluation_criteria:
    metadata:
      concept: "Critérios para checkpoint EvaluateForEnrich"
      governance_rules: |
        [Definição de quando conhecimento deve ser enriquecido]
    nodes:
      - id: "relevance"
        label: "Relevância"
        parent: null
        level: 0
        governance:
          threshold: "medium"
          evaluators: ["domain_experts"]
      - id: "reusability"
        label: "Reusabilidade"
        parent: null
        level: 0
        governance:
          threshold: "high"
          evaluators: ["architects"]
      - id: "impact"
        label: "Impacto"
        parent: null
        level: 0
        governance:
          threshold: "medium"
          evaluators: ["stakeholders"]

governance:
  version_control:
    change_approval_required: true
    change_authority: "architecture_committee"
    impact_analysis_required: true
  
  audit_trail:
    track_changes: true
    change_notifications: ["all_users"]
    validation_frequency_days: 90
  
  conflict_resolution:
    escalation_path: ["team_lead", "architecture_committee", "cto"]
    resolution_timeout_days: 14
```

---

## 🔄 Integração com Componentes Matrix

### MEF Integration

**Campos MOC no MEF:**
```yaml
scope_ref: "team"
scope_mode: "restricted"  # ou "propagated"
domain_ref: "technical"
type_ref: "pattern"
maturity_ref: "approved"
```

**Resolução Automática:**
- Sistema consulta MOC para validar referências
- Aplica regras de governança automaticamente
- Propaga mudanças conforme configuração

### ZWF Integration

**Checkpoint EvaluateForEnrich:**
```yaml
flow_execution:
  - state: "evaluate_for_enrich"
    signals:
      context: "Avaliando se conhecimento gerado deve enriquecer Oracle"
      criteria_refs: ["relevance", "reusability", "impact"]
      decision: "Baseado em critérios MOC específicos da organização"
      result: "Aprovado para enriquecimento com escopo 'team'"
```

### OIF Integration

**Controle de Acesso:**
- Resolução de pertinência baseada em `scope_ref` do usuário
- Filtragem automática por `domain_ref` e autoridade
- Explicabilidade referenciando nós MOC específicos

---

## 📚 Governança e Versionamento

### Controle de Mudanças

**Impacto de Alterações:**
- **Adição de nós**: Impacto baixo, retrocompatível
- **Modificação de hierarquia**: Impacto médio, validação necessária
- **Remoção de nós**: Impacto alto, análise de dependências obrigatória

**Processo de Atualização:**
1. Proposta de mudança com análise de impacto
2. Validação de UKIs dependentes
3. Aprovação pela autoridade competente
4. Versionamento e notificação
5. Período de migração para dependentes

### Auditabilidade

**Rastros Obrigatórios:**
- Histórico completo de versões MOC
- Registro de quem aprovou cada mudança
- Análise de impacto em UKIs existentes
- Notificações automáticas para afetados

---

## 🎯 Benefícios do MOC

### Para Organizações
- **Flexibilidade Total**: Adapt estruturas às necessidades específicas
- **Governança Transparente**: Regras claras e auditáveis
- **Evolução Orgânica**: Mudanças organizacionais não quebram o protocolo

### Para o Protocolo Matrix
- **Coerência Conceitual**: Conceitos universais mantidos
- **Interoperabilidade**: Diferentes organizações podem compartilhar conhecimento
- **Escalabilidade**: De equipes pequenas a grandes corporações

### Para IA e Automação
- **Contexto Rico**: IA entende hierarquias organizacionais específicas
- **Decisões Inteligentes**: Automação baseada em regras de governança locais
- **Explicabilidade**: Transparência total sobre decisões baseadas no MOC

---

<a name="english"></a>
# English 🇺🇸

> 🚨 **IMPORTANT WARNING**: This document contains ILLUSTRATIVE EXAMPLES (such as `technical`, `business`, `draft`, etc.) that are NOT mandatory taxonomies. Each organization defines its own hierarchies according to their specific needs. Examples serve only as conceptual reference.

> "Local flexibility preserves global coherence."

---

## 🌐 MOC Overview

The **Matrix Ontology Catalog (MOC)** is the fundamental component that allows the Matrix Protocol to separate universal core concepts from organization-specific taxonomies and structures.

MOC defines **configurable hierarchies** for any concept that depends on organizational structures, maintaining global conceptual consistency while enabling total local adaptability.

---

## 📋 Fundamental Principles

### 🔧 Conceptual Separation

**Core Concepts (Universal)**
- Fixed and immutable across all implementations
- Examples: scope, domain, maturity, propagation, workflow checkpoints
- Defined by the Matrix Protocol

**Local Taxonomies (Configurable)**
- Defined by the implementer in the MOC
- Examples: specific scope names, domain structure, organizational roles
- Adaptable to organizational context

### 🏗️ Configurable Semantic Hierarchies

Every hierarchical concept must:
- Be conceptually defined by the protocol
- Have its concrete hierarchy provided by the MOC
- Allow reorganization without breaking MEF, ZWF, or OIF
- Maintain stable semantic relationships

---

## 🗂️ MOC Structure

### Base Format

```yaml
csh_version: "1.0"
organization: "[Organization Name]"
created_date: "[YYYY-MM-DD]"
last_modified: "[YYYY-MM-DD]"
version: "[MAJOR.MINOR.PATCH]"

hierarchies:
  scope:
    metadata:
      concept: "Knowledge reach and visibility"
      governance_rules: |
        [Governance rules for scopes]
    nodes:
      - id: "personal"
        label: "Personal"
        parent: null
        level: 0
        governance:
          visibility: ["owner"]
          propagation: "none"
          authority_required: "self"
      - id: "team"
        label: "Team"
        parent: "personal"
        level: 1
        governance:
          visibility: ["team_members"]
          propagation: "restricted"
          authority_required: "team_lead"
      - id: "organization"
        label: "Organization"
        parent: "team"
        level: 2
        governance:
          visibility: ["all_members"]
          propagation: "automatic"
          authority_required: "architecture_committee"

  domain:
    metadata:
      concept: "Knowledge area and specialization"
      governance_rules: |
        [Domain classification and ownership rules]
    nodes:
      - id: "technical"
        label: "Technical"
        parent: null
        level: 0
        governance:
          owners: ["engineering"]
          reviewers: ["tech_leads", "architects"]
      - id: "business"
        label: "Business"
        parent: null
        level: 0
        governance:
          owners: ["product_managers", "business_analysts"]
          reviewers: ["stakeholders"]

  maturity:
    metadata:
      concept: "Validation and reliability level"
      governance_rules: |
        [Criteria for progression between levels]
    nodes:
      - id: "draft"
        label: "Draft"
        parent: null
        level: 0
        governance:
          auto_promotion: false
          validation_required: false
      - id: "review"
        label: "Review"
        parent: "draft"
        level: 1
        governance:
          auto_promotion: false
          validation_required: true
          reviewers_required: 2
      - id: "approved"
        label: "Approved"
        parent: "review"
        level: 2
        governance:
          auto_promotion: false
          validation_required: true
          authority_required: "domain_owner"

  evaluation_criteria:
    metadata:
      concept: "Criteria for EvaluateForEnrich checkpoint"
      governance_rules: |
        [Definition of when knowledge should be enriched]
    nodes:
      - id: "relevance"
        label: "Relevance"
        parent: null
        level: 0
        governance:
          threshold: "medium"
          evaluators: ["domain_experts"]
      - id: "reusability"
        label: "Reusability"
        parent: null
        level: 0
        governance:
          threshold: "high"
          evaluators: ["architects"]
      - id: "impact"
        label: "Impact"
        parent: null
        level: 0
        governance:
          threshold: "medium"
          evaluators: ["stakeholders"]

governance:
  version_control:
    change_approval_required: true
    change_authority: "architecture_committee"
    impact_analysis_required: true
  
  audit_trail:
    track_changes: true
    change_notifications: ["all_users"]
    validation_frequency_days: 90
  
  conflict_resolution:
    escalation_path: ["team_lead", "architecture_committee", "cto"]
    resolution_timeout_days: 14
```

---

## 🔄 Matrix Components Integration

### MEF Integration

**MOC Fields in MEF:**
```yaml
scope_ref: "team"
scope_mode: "restricted"  # or "propagated"
domain_ref: "technical"
type_ref: "pattern"
maturity_ref: "approved"
```

**Automatic Resolution:**
- System consults MOC to validate references
- Applies governance rules automatically
- Propagates changes according to configuration

### ZWF Integration

**EvaluateForEnrich Checkpoint:**
```yaml
flow_execution:
  - state: "evaluate_for_enrich"
    signals:
      context: "Evaluating if generated knowledge should enrich Oracle"
      criteria_refs: ["relevance", "reusability", "impact"]
      decision: "Based on organization-specific MOC criteria"
      result: "Approved for enrichment with 'team' scope"
```

### OIF Integration

**Access Control:**
- Pertinence resolution based on user's `scope_ref`
- Automatic filtering by `domain_ref` and authority
- Explainability referencing specific MOC nodes

---

## 📚 Governance and Versioning

### Change Control

**Change Impact:**
- **Node addition**: Low impact, backward compatible
- **Hierarchy modification**: Medium impact, validation required
- **Node removal**: High impact, mandatory dependency analysis

**Update Process:**
1. Change proposal with impact analysis
2. Dependent UKI validation
3. Approval by competent authority
4. Versioning and notification
5. Migration period for dependents

### Auditability

**Mandatory Trails:**
- Complete MOC version history
- Record of who approved each change
- Impact analysis on existing UKIs
- Automatic notifications to affected parties

---

## 🎯 MOC Benefits

### For Organizations
- **Total Flexibility**: Adapt structures to specific needs
- **Transparent Governance**: Clear and auditable rules
- **Organic Evolution**: Organizational changes don't break the protocol

### For Matrix Protocol
- **Conceptual Coherence**: Universal concepts maintained
- **Interoperability**: Different organizations can share knowledge
- **Scalability**: From small teams to large corporations

### For AI and Automation
- **Rich Context**: AI understands specific organizational hierarchies
- **Intelligent Decisions**: Automation based on local governance rules
- **Explainability**: Complete transparency about MOC-based decisions

---