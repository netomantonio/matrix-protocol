# 📜 ZWF WORKFLOW EXAMPLES | EXEMPLOS DE FLUXOS ZWF

## 🌎 Idioma / Language

- [Português 🇧🇷](#português)
- [English 🇺🇸](#english)

---

<a name="português"></a>
# Português 🇧🇷

# Exemplos de Fluxos ZWF - Zion Workflow Framework

Esta pasta contém exemplos práticos de fluxos ZWF (Zion Workflow Framework) demonstrando como implementar os padrões conceituais definidos na especificação.

## 📁 Estrutura dos Exemplos

### 🔧 Request Flow (work.proposed)
- **zwf-jwt-implementation-pt.yaml** - Versão em Português
- **zwf-jwt-implementation-en.yaml** - Versão em Inglês

**Contexto:** Implementação de autenticação seguindo estados canônicos ZWF  
**Domínio:** Técnico  

Demonstra um fluxo completo de implementação técnica:
- Consulta ao Oráculo para padrões de segurança
- Decisão baseada em UKIs existentes
- Execução com processo de review
- Enriquecimento com exemplos práticos e novos padrões

### 📈 Refinement Flow (work.refine.requested)
- **zwf-onboarding-refinement-pt.yaml** - Versão em Português  
- **zwf-onboarding-refinement-en.yaml** - Versão em Inglês

**Contexto:** Refinamento de produto com abordagem incremental  
**Domínio:** Produto

Exemplifica refinamento incremental baseado em dados:
- Análise de dados vs diretrizes do Oráculo
- Abordagem incremental fundamentada em UKIs
- Atualização de UKI existente com nova versão
- Criação de padrão de refinement reutilizável

### 📚 Ingestion Flow (knowledge.added)
- **zwf-knowledge-ingestion-pt.yaml** - Versão em Português
- **zwf-knowledge-ingestion-en.yaml** - Versão em Inglês

**Contexto:** Processamento de documentação externa  
**Domínio:** Técnico

Mostra como processar conhecimento externo estruturadamente:
- Análise seletiva focada em impacto crítico
- Estruturação de mudanças significativas como UKIs
- Criação de guias de migração práticos
- Relacionamentos semânticos entre conhecimentos

---

## 🎯 Padrões ZWF Demonstrados

### Estados Canônicos
- **Intake:** Captura e organiza contexto inicial
- **Understand:** Consulta estruturada ao Oráculo com UKIs específicas
- **Decide:** Decisões baseadas em conhecimento existente
- **Act:** Execução usando ferramentas da equipe
- **Review:** Validação humana quando aplicável
- **Evaluate_for_enrich:** Avalia critérios para enriquecimento do Oráculo
- **Enrich:** Criação/atualização obrigatória de UKIs

### Tipos de Evento
- `work.proposed` → Implementação de nova funcionalidade
- `work.refine.requested` → Melhoria de processo existente
- `knowledge.added` → Ingestão de documentação externa

### Relacionamentos com Oráculo
- **Entrada:** Consulta de UKIs para fundamentar decisões
- **Saída:** Criação/atualização de UKIs relacionados
- **Rastreabilidade:** Campo `related_to` com relacionamentos semânticos tipados

### Relacionamentos Semânticos Tipados
Todos os exemplos demonstram o novo formato de relacionamentos tipados:

```yaml
related_to:
  - target: unik-target-id
    relation_type: implements|depends_on|extends|replaces|complies_with|conflicts_with|derives_from|relates_to
    description: Descrição clara da relação
```

**Tipos utilizados nos exemplos:**
- `implements` - Implementa padrões ou regras
- `complies_with` - Segue políticas ou padrões
- `extends` - Estende conceitos existentes
- `derives_from` - Derivado de conhecimento base
- `relates_to` - Relacionamento contextual geral

---

## 🔍 Como Usar Estes Exemplos

### Para Equipes
1. **Escolha o padrão** mais similar ao seu fluxo atual
2. **Adapte os campos** para seu contexto específico
3. **Mantenha a estrutura** de estados canônicos
4. **Implemente com suas ferramentas** preferidas

### Para Implementação de Sistemas
1. **Extraia os metadados** de rastreabilidade
2. **Implemente coleta** dos sinais de explicabilidade
3. **Integre com seu Oráculo** (repositório de UKIs)
4. **Configure alertas** para enriquecimento obrigatório

### Para Auditoria e Governança
1. **Verifique relacionamentos** entre UKIs motivadoras e geradas
2. **Analise tempos** entre estados para otimização
3. **Valide cobertura** de conhecimento crítico
4. **Monitore qualidade** do enriquecimento

---

## ⚙️ Adaptação para Tecnologias

Estes exemplos são **independentes de tecnologia**. Cada equipe pode implementar usando:

**Workflow Engines:**
- GitHub Actions (eventos de repositório)
- Jenkins (pipelines com stages)
- Airflow (DAGs com sensores)
- Azure DevOps (work items + pipelines)

**Tracking Systems:**
- Jira (custom fields para sinais ZWF)
- Linear (estados customizados)
- Monday.com (boards com automações)
- Notion (databases com relacionamentos)

**Knowledge Bases:**
- GitLab/GitHub (arquivos YAML + relacionamentos)
- Confluence (páginas com metadata)
- Obsidian (markdown com links semânticos)
- Databases (PostgreSQL + embeddings)

---

## 📊 Métricas Canônicas de Telemetria

Todos os exemplos incluem **métricas de telemetria padronizadas** para observabilidade e monitoramento de workflows ZWF.

### 🕘 Métricas de Tempo entre Estados
- **Timestamps precisos:** Início e fim de cada transição
- **Duração em segundos:** Tempo real gasto em cada estado
- **Tempo total:** Duração completa do workflow

### 📈 Métricas de Qualidade de Transições
- **Score geral:** 0-100 indicando qualidade do workflow
- **Scores por estado:** Avaliação individual de cada estado canônico
- **Fatores de qualidade:**
  - `oracle_coverage`: % de decisões fundamentadas em UKIs
  - `explainability_depth`: Nível de detalhamento dos sinais
  - `relationship_clarity`: Clareza dos relacionamentos `related_to`

### 🏥 Métricas de Health do Workflow
- **Status de conclusão:** successful | failed | partial
- **Contadores:** Erros, warnings, retries
- **Cobertura de estados:** Estados executados vs. esperados
- **Disponibilidade do Oráculo:** Estado da consulta a UKIs
- **Sucesso do enriquecimento:** Confirmação da atualização

### 🔮 Métricas de Eficiência do Enriquecimento
- **UKIs consultadas vs. criadas:** Proporção entrada/saída
- **Contagem de relacionamentos:** Densidade semântica
- **Domínios tocados:** Abrangência do conhecimento
- **Score de coerência semântica:** 0-100 para qualidade
- **Potencial de reutilização:** Estimativa de valor futuro

### 🎯 Indicadores de Performance
- **Throughput score:** Balanceamento velocidade vs. qualidade
- **Efficiency ratio:** Tempo útil sobre tempo total
- **Oracle hit rate:** Taxa de UKIs encontrados
- **Decision confidence:** Confiança nas decisões tomadas

### 🏷️ Tags de Observabilidade
- **Team:** Identificação da equipe
- **Trigger type:** Tipo de evento inicial
- **Complexity level:** Estimativa de complexidade
- **AI assistance level:** Nível de assistência de IA
- **Feature/business criticality:** Criticidade do negócio

### Estrutura Completa
```yaml
telemetry:
  workflow_id: "identificador-unico"
  execution_start: "2024-01-15T09:00:00Z"
  execution_end: "2024-01-15T16:30:00Z"
  total_duration_seconds: 27000
  
  state_transition_duration: [tempos por transição]
  transition_quality_score: [scores de qualidade]
  workflow_health_metrics: [indicadores de saúde]
  oracle_enrichment_metrics: [métricas de enriquecimento]
  performance_indicators: [indicadores de performance]
  observability_tags: [tags para categorização]
```

---

## 📊 Elementos Conceituais Demonstrados

### Conformidade com ZWF
- Todos os fluxos seguem estados canônicos
- Eventos iniciais são de tipos reconhecidos pelo ZWF
- Consultas ao Oráculo documentadas e justificadas
- Sinais de explicabilidade registrados

### Qualidade do Conhecimento
- UKIs criadas/atualizadas seguem formato MEF
- Relacionamentos `related_to` conectam aprendizados
- Rastreabilidade mantida entre motivação e resultado

### Completude Conceitual
- Ciclo fechado: Consultar → Agir → Enriquecer
- Aprendizados capturados e estruturados
- Processo replicável documentado

---

> **Atenção:** Para dúvidas sobre implementação, consulte a especificação completa em [`ZWF_ZION_WORKFLOW_FRAMEWORK.md`](../ZWF_ZION_WORKFLOW_FRAMEWORK.md).

---

<a name="english"></a>
# English 🇺🇸

# ZWF Flow Examples - Zion Workflow Framework

This folder contains practical examples of ZWF (Zion Workflow Framework) flows demonstrating how to implement the conceptual patterns defined in the specification.

## 📁 Examples Structure

### 🔧 Request Flow (work.proposed)
- **zwf-jwt-implementation-pt.yaml** - Portuguese Version
- **zwf-jwt-implementation-en.yaml** - English Version

**Context:** Authentication implementation following ZWF canonical states  
**Domain:** Technical  

Demonstrates a complete technical implementation flow:
- Oracle consultation for security patterns
- Decision based on existing UKIs
- Execution with review process
- Enrichment with practical examples and new patterns

### 📈 Refinement Flow (work.refine.requested)
- **zwf-onboarding-refinement-pt.yaml** - Portuguese Version
- **zwf-onboarding-refinement-en.yaml** - English Version

**Context:** Product refinement with incremental approach  
**Domain:** Product

Exemplifies incremental refinement based on data:
- Data analysis vs Oracle guidelines
- Incremental approach based on UKIs
- Update existing UKI with new version
- Creation of reusable refinement pattern

### 📚 Ingestion Flow (knowledge.added)
- **zwf-knowledge-ingestion-pt.yaml** - Portuguese Version
- **zwf-knowledge-ingestion-en.yaml** - English Version

**Context:** External documentation processing  
**Domain:** Technical

Shows how to process external knowledge in a structured way:
- Selective analysis focused on critical impact
- Structuring significant changes as UKIs
- Creating practical migration guides
- Semantic relationships between knowledge

---

## 🎯 ZWF Patterns Demonstrated

### Canonical States
- **Intake:** Capture and organize initial context
- **Understand:** Structured Oracle consultation with specific UKIs
- **Decide:** Decisions based on existing knowledge
- **Act:** Execution using team tools
- **Review:** Human validation when applicable
- **Evaluate_for_enrich:** Evaluates criteria for Oracle enrichment
- **Enrich:** Mandatory UKI creation/update

### Event Types
- `work.proposed` → New functionality implementation
- `work.refine.requested` → Existing process improvement
- `knowledge.added` → External documentation ingestion

### Oracle Relationships
- **Input:** UKI queries to support decisions
- **Output:** Creation/update of related UKIs
- **Traceability:** `related_to` field with typed semantic relationships

### Typed Semantic Relationships
All examples demonstrate the new typed relationship format:

```yaml
related_to:
  - target: unik-target-id
    relation_type: implements|depends_on|extends|replaces|complies_with|conflicts_with|derives_from|relates_to
    description: Clear description of the relationship
```

**Types used in examples:**
- `implements` - Implements patterns or rules
- `complies_with` - Follows policies or standards
- `extends` - Extends existing concepts
- `derives_from` - Derived from base knowledge
- `relates_to` - General contextual relationship

---

## 🔍 How to Use These Examples

### For Teams
1. **Choose the pattern** most similar to your current flow
2. **Adapt the fields** to your specific context
3. **Maintain the structure** of canonical states
4. **Implement with your preferred tools**

### For System Implementation
1. **Extract metadata** for traceability
2. **Implement collection** of explainability signals
3. **Integrate with your Oracle** (UKI repository)
4. **Configure alerts** for mandatory enrichment

### For Audit and Governance
1. **Verify relationships** between motivating and generated UKIs
2. **Analyze times** between states for optimization
3. **Validate coverage** of critical knowledge
4. **Monitor quality** of enrichment

---

## ⚙️ Technology Adaptation

These examples are **technology-independent**. Each team can implement using:

**Workflow Engines:**
- GitHub Actions (repository events)
- Jenkins (pipelines with stages)
- Airflow (DAGs with sensors)
- Azure DevOps (work items + pipelines)

**Tracking Systems:**
- Jira (custom fields for ZWF signals)
- Linear (custom states)
- Monday.com (boards with automations)
- Notion (databases with relationships)

**Knowledge Bases:**
- GitLab/GitHub (YAML files + relationships)
- Confluence (pages with metadata)
- Obsidian (markdown with semantic links)
- Databases (PostgreSQL + embeddings)

---

## 📊 Canonical Telemetry Metrics

All examples include **standardized telemetry metrics** for ZWF workflow observability and monitoring.

### 🕘 State Transition Duration Metrics
- **Precise timestamps:** Start and end of each transition
- **Duration in seconds:** Real time spent in each state
- **Total time:** Complete workflow duration

### 📈 Transition Quality Metrics
- **Overall score:** 0-100 indicating workflow quality
- **State scores:** Individual evaluation of each canonical state
- **Quality factors:**
  - `oracle_coverage`: % of decisions founded on UKIs
  - `explainability_depth`: Signal detail level
  - `relationship_clarity`: Clarity of `related_to` relationships

### 🏥 Workflow Health Metrics
- **Completion status:** successful | failed | partial
- **Counters:** Errors, warnings, retries
- **State coverage:** Executed vs. expected states
- **Oracle availability:** UKI consultation status
- **Enrichment success:** Update confirmation

### 🔮 Oracle Enrichment Efficiency Metrics
- **UKIs consulted vs. created:** Input/output ratio
- **Relationship count:** Semantic density
- **Domains touched:** Knowledge breadth
- **Semantic coherence score:** 0-100 for quality
- **Reusability potential:** Future value estimate

### 🎯 Performance Indicators
- **Throughput score:** Speed vs. quality balance
- **Efficiency ratio:** Useful time over total time
- **Oracle hit rate:** Rate of UKIs found
- **Decision confidence:** Confidence in decisions made

### 🏷️ Observability Tags
- **Team:** Team identification
- **Trigger type:** Initial event type
- **Complexity level:** Complexity estimate
- **AI assistance level:** Level of AI assistance
- **Feature/business criticality:** Business criticality

### Complete Structure
```yaml
telemetry:
  workflow_id: "unique-identifier"
  execution_start: "2024-01-15T09:00:00Z"
  execution_end: "2024-01-15T16:30:00Z"
  total_duration_seconds: 27000
  
  state_transition_duration: [times per transition]
  transition_quality_score: [quality scores]
  workflow_health_metrics: [health indicators]
  oracle_enrichment_metrics: [enrichment metrics]
  performance_indicators: [performance indicators]
  observability_tags: [categorization tags]
```

---

## 📊 Demonstrated Conceptual Elements

### ZWF Compliance
- All flows follow canonical states
- Initial events are ZWF-recognized types
- Oracle consultations documented and justified
- Explainability signals recorded

### Knowledge Quality
- Created/updated UKIs follow MEF format
- `related_to` relationships connect learnings
- Traceability maintained between motivation and result

### Conceptual Completeness
- Closed loop: Query → Act → Enrich
- Learnings captured and structured
- Replicable process documented

---

> **Warning:** For implementation questions, consult the complete specification at [`ZWF_ZION_WORKFLOW_FRAMEWORK.md`](../ZWF_ZION_WORKFLOW_FRAMEWORK.md).