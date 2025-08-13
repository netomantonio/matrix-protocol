# 📜 MATRIX ZWF PROTOCOL | PROTOCOLO MATRIX ZWF

## 🌎 Idioma / Language

- [Português 🇧🇷](#português)
- [English 🇺🇸](#english)

---

<a name="português"></a>
# Português 🇧🇷

> Zion Workflow Framework

**Versão:** 1.0
**Status:** Ativo
**Finalidade:** Especificar de forma conceitual e padronizada o framework de fluxos de trabalho para equipes orientadas a IA, definindo como descrever, executar e governar workflows como máquinas de estado independentes de tecnologia.

---

## 📟️ VISÃO GERAL

O Protocolo Matrix ZWF define um **modelo conceitual para fluxos de trabalho orientados a IA** que permite que equipes multidisciplinares descrevam workflows como máquinas de estado independentes de tecnologia. Todos os fluxos seguem o padrão: **Evento → Consulta Oráculo → Decisão → Ação → Enriquecimento do Oráculo**.

O ZWF não prescreve ferramentas, motores de orquestração ou implementações técnicas - apenas direciona **como pensar e registrar o caminho** de forma conceitual e rastreável.

---

## 🎭 ATORES E PAPÉIS

### 🔮 **Oráculo**
- **Função:** Repositório estratégico/semântico que mantém UKIs (MEF)
- **Entrada:** Consultas para diretrizes, regras, decisões, padrões e exemplos
- **Saída:** Conhecimento contextual para fundamentar decisões nos fluxos
- **Enriquecimento:** Recebe novos/atualizados UKIs ao final dos fluxos

### 👥 **Equipes**
- **Função:** Descrevem fluxos em linguagem conceitual ZWF
- **Responsabilidade:** Implementam os fluxos usando suas próprias ferramentas e tecnologias
- **Papéis:** Dev/Eng/Tech/PM/UX/Analistas

### ⚙️ **Operador**
- **Função:** Executa na prática (CI/CD, IDE, orquestradores, etc.)
- **Limitação:** ZWF não prescreve como implementar - apenas o que desenhar

---

## 📡 EVENTOS CANÔNICOS (GATILHOS)

O ZWF reconhece seis tipos de eventos que iniciam fluxos:

| Evento | Descrição | Contexto Típico |
|--------|-----------|-----------------|
| `knowledge.added` | Novo conteúdo disponível | Documentação, especificações, decisões |
| `work.proposed` | Nova proposta de trabalho | História, épico, feature, estratégia |
| `work.refine.requested` | Solicitação de refinamento | Melhorias, ajustes, otimizações |
| `assistance.requested` | Pedido de ajuda/colaboração | Pair programming, consultoria, suporte |
| `test.authored` | Cenários de teste criados | Testes unitários, integração, aceitação |
| `feedback.submitted` | Correção/aprendizado | Bug reports, melhorias, lições aprendidas |

---

## 🔄 ESTADOS CANÔNICOS (MÁQUINA DE ESTADO)

Todo fluxo ZWF segue esta sequência conceitual obrigatória:

```mermaid
stateDiagram-v2
    [*] --> Intake
    Intake --> Understand
    Understand --> Decide
    Decide --> Act
    Act --> Review
    Act --> Enrich
    Review --> Enrich
    Enrich --> [*]
    
    note right of Understand
      Consulta UKIs do Oráculo
      para interpretação
    end note
    
    note right of Review
      Estado opcional
      Intervenção humana
    end note
    
    note right of Enrich
      Obrigatório
      Devolve aprendizado
      como UKIs MEF
    end note
```

### 📨 **Intake**
- **Propósito:** Receber o evento e organizar o contexto
- **Ações:** Capturar dados do evento, validar formato, preparar contexto
- **Saída:** Contexto estruturado para consulta ao Oráculo

### 🧠 **Understand (via Oráculo)**
- **Propósito:** Consultar UKIs pertinentes para interpretar intenção/risco/contexto
- **Ações:** Busca semântica no Oráculo, análise de UKIs relacionados
- **Saída:** Conhecimento contextual para fundamentar decisões

### ⚖️ **Decide**
- **Propósito:** Escolher caminho baseado nas diretrizes do Oráculo
- **Ações:** Aplicar regras de negócio, avaliar riscos, definir ações
- **Saída:** Plano de ação fundamentado em UKIs

### 🎯 **Act**
- **Propósito:** Executar a ação com pessoas, agentes ou ferramentas
- **Ações:** Implementação prática usando recursos disponíveis da equipe
- **Saída:** Resultado da execução + contexto de aprendizado

### 👁️ **Review (Opcional)**
- **Propósito:** Intervenção humana quando necessário
- **Ações:** Validação humana, aprovação, ajustes
- **Saída:** Confirmação ou redirecionamento

### 🔄 **Enrich Oracle (Obrigatório)**
- **Propósito:** Devolver aprendizado como UKIs MEF válidos
- **Ações:** Criar/atualizar UKIs referenciais ao que motivou o fluxo
- **Saída:** Conhecimento estruturado adicionado ao Oráculo

---

## 🔗 VÍNCULO AO ORÁCULO

### 📋 **Declaração Inicial**
Todo fluxo deve declarar no início quais UKIs do Oráculo o motivam:

```yaml
# Exemplo de declaração de fluxo
flow_id: zion-workflow-jwt-implementation
triggered_by: work.proposed
oracle_context:
  motivating_ukis:
    - unik-technical-jwt-authentication-pattern
    - unik-business-security-requirements
    - unik-culture-code-review-process
```

### ⚖️ **Fundamentação de Decisões**
Durante as transições, o fluxo deve explicitar quais UKIs fundamentam cada decisão:

```yaml
# Exemplo de decisão fundamentada
decision_point: "choose_jwt_library"
reasoning_ukis:
  - unik-technical-jwt-security-standards
  - unik-business-vendor-approval-policy
decision_outcome: "use_jsonwebtoken_library"
```

### 🔄 **Enriquecimento Obrigatório**
As saídas devem referenciar UKIs motivadores através do campo `related_to`:

```yaml
# Exemplo de UKI gerada no enriquecimento
id: unik-technical-jwt-implementation-result
related_to:
  - unik-technical-jwt-authentication-pattern  # UKI motivador
  - unik-business-security-requirements        # UKI motivador
content: |
  Implementação bem-sucedida do padrão JWT seguindo as diretrizes de segurança.
  Baseado nas orientações dos UKIs relacionados, adaptado para nosso contexto específico.
```

---

## 📤 SAÍDAS OBRIGATÓRIAS

### 🎯 **Tipos de Saída MEF**
Todo fluxo deve retornar algo ao Oráculo escolhendo entre os tipos MEF:

| Tipo UKI | Quando Usar | Exemplo de Saída |
|----------|-------------|------------------|
| `business_rule` | Regra estabelecida | Nova política de autenticação |
| `guideline` | Diretriz consolidada | Processo de code review atualizado |
| `pattern` | Prática padronizada | Padrão de implementação de API |
| `decision` | Decisão registrada | Escolha de tecnologia documentada |
| `template` | Modelo reutilizável | Template de configuração |
| `function` | Implementação específica | Função de validação JWT |
| `example` | Caso de uso documentado | Exemplo de uso da API |

### 🔗 **Relacionamentos Obrigatórios**
Cada UKI gerada deve incluir:
- `related_to`: UKIs que motivaram/impactaram o fluxo
- Resumo claro da intenção da relação no campo `content`

---

## 📊 EXPLICABILIDADE MÍNIMA

Em cada estado do fluxo, registrar três sinais em linguagem natural:

### 📝 **Template de Registro**
```yaml
flow_step: [nome_do_estado]
signals:
  context: "O que entrou: [descrição da entrada]"
  decision: "Por que transicionou: [justificativa baseada em UKIs do Oráculo]" 
  result: "O que saiu: [descrição da saída]"
oracle_ukis_used:
  - unik-[id-do-uki-consultado]
timestamp: [YYYY-MM-DD HH:MM:SS]
```

### 💡 **Exemplo Prático**
```yaml
flow_step: "decide"
signals:
  context: "Recebida solicitação para implementar autenticação JWT na API"
  decision: "Escolhido padrão bearer token baseado no unik-technical-jwt-authentication-pattern que especifica melhores práticas de segurança"
  result: "Definido usar biblioteca jsonwebtoken com configuração de expiração de 15 minutos"
oracle_ukis_used:
  - unik-technical-jwt-authentication-pattern
  - unik-business-token-expiration-policy
timestamp: "2024-01-15 14:30:22"
```

---

## 📊 MÉTRICAS CANÔNICAS DE TELEMETRIA

Para observabilidade e monitoramento efetivo de workflows ZWF, estabelecemos métricas padronizadas que devem ser coletadas durante a execução de cada fluxo.

### 🕘 **Métricas de Tempo entre Estados**
```yaml
state_transition_duration:
  intake_to_understand: 
    timestamp_start: "2024-01-15T14:30:22Z"
    timestamp_end: "2024-01-15T14:32:15Z"
    duration_seconds: 113
  understand_to_decide:
    timestamp_start: "2024-01-15T14:32:15Z"
    timestamp_end: "2024-01-15T14:35:48Z"
    duration_seconds: 213
  decide_to_act:
    timestamp_start: "2024-01-15T14:35:48Z"
    timestamp_end: "2024-01-15T14:45:30Z"
    duration_seconds: 582
  act_to_review:
    timestamp_start: "2024-01-15T14:45:30Z"
    timestamp_end: "2024-01-15T14:48:12Z"
    duration_seconds: 162
  review_to_enrich:
    timestamp_start: "2024-01-15T14:48:12Z"
    timestamp_end: "2024-01-15T14:50:05Z"
    duration_seconds: 113
```

### 📈 **Métricas de Qualidade de Transições**
```yaml
transition_quality_score:
  overall_workflow_score: 85  # 0-100
  state_scores:
    intake: 90     # Completude da captura de contexto
    understand: 88 # Qualidade da consulta ao Oráculo
    decide: 82     # Fundamentação das decisões
    act: 85        # Eficácia da execução
    review: 95     # Qualidade da validação
    enrich: 78     # Qualidade do UKI gerado
  quality_factors:
    oracle_coverage: 85      # % de decisões fundamentadas em UKIs
    explainability_depth: 90 # Detalhamento dos sinais
    relationship_clarity: 80 # Clareza dos related_to
```

### 🏥 **Métricas de Health do Workflow**
```yaml
workflow_health_metrics:
  completion_status: "successful"  # successful | failed | partial
  error_count: 0
  warning_count: 2
  retry_count: 1
  state_coverage: 
    total_states: 6
    executed_states: 6
    skipped_states: 0
  oracle_availability: "available"  # available | degraded | unavailable
  enrichment_success: true
```

### 🔮 **Métricas de Eficiência do Enriquecimento**
```yaml
oracle_enrichment_metrics:
  ukis_consulted: 5
  ukis_created: 1
  ukis_updated: 0
  relationship_count: 3
  knowledge_domains_touched:
    - technical
    - business
  semantic_coherence_score: 87  # 0-100
  reusability_potential: "high"  # low | medium | high
```

### 📋 **Template Completo de Métricas**
```yaml
telemetry:
  workflow_id: "zwf-jwt-implementation-001"
  execution_start: "2024-01-15T14:30:22Z"
  execution_end: "2024-01-15T14:50:05Z"
  total_duration_seconds: 1183
  
  state_transition_duration: [estrutura acima]
  transition_quality_score: [estrutura acima]
  workflow_health_metrics: [estrutura acima]
  oracle_enrichment_metrics: [estrutura acima]
  
  performance_indicators:
    throughput_score: 85        # Velocidade vs. qualidade
    efficiency_ratio: 0.73      # Tempo útil / tempo total
    oracle_hit_rate: 0.89       # UKIs encontrados / UKIs buscados
    decision_confidence: 0.85   # Confiança nas decisões tomadas
  
  observability_tags:
    team: "backend-squad"
    trigger_type: "work.proposed"
    complexity_level: "medium"   # low | medium | high
    ai_assistance_level: "high"  # none | low | medium | high
```

---

## ⚖️ INVARIANTES DE ESTADO (FORMAL)

Para garantir a execução robusta e determinística, cada estado ZWF deve atender invariantes conceituais que podem ser implementados por engines duráveis:

### 📋 **Invariantes por Estado**

#### 📨 **Intake State**
```yaml
preconditions:
  - trigger_event: defined
  - event_type: valid_canonical_event
postconditions:
  - context_structured: true
  - trigger_validated: true
  - oracle_context_prepared: true
validation:
  required_fields: [flow_id, triggered_by, oracle_context]
  context_format: structured
```

#### 🧠 **Understand State**
```yaml
preconditions:
  - intake_completed: true
  - context_structured: true
postconditions:
  - oracle_consulted: true
  - ukis_identified: min_1
  - strategy_defined: true
validation:
  required_ukis: min_1
  oracle_response: structured
  understanding_documented: true
```

#### ⚖️ **Decide State**
```yaml
preconditions:
  - understanding_completed: true
  - oracle_knowledge_available: true
postconditions:
  - decision_made: true
  - reasoning_documented: true
  - action_plan_defined: true
validation:
  decision_rationale: required
  reasoning_ukis: min_1
  action_plan: structured
```

#### 🎯 **Act State**
```yaml
preconditions:
  - decision_made: true
  - action_plan_defined: true
postconditions:
  - action_executed: true
  - execution_result: documented
  - learning_context_captured: true
validation:
  execution_evidence: required
  result_documentation: structured
  error_handling: documented
```

#### 👁️ **Review State (Optional)**
```yaml
preconditions:
  - action_executed: true
  - review_required: true
postconditions:
  - validation_completed: true
  - approval_status: defined
  - feedback_documented: true
validation:
  review_criteria: defined
  reviewer_input: documented
  outcome_clear: true
```

#### 🔄 **Enrich State (Mandatory)**
```yaml
preconditions:
  - workflow_completed: true
  - learning_captured: true
postconditions:
  - uki_created: true
  - oracle_updated: true
  - relationships_established: true
validation:
  uki_format: mef_compliant
  related_to: motivating_ukis_referenced
  content_meaningful: true
```

### 🔄 **Invariantes de Transição**

#### **Estado para Estado**
```yaml
# Regras gerais de transição
transition_rules:
  intake_to_understand:
    condition: context_structured AND oracle_context_prepared
  understand_to_decide:
    condition: oracle_consulted AND strategy_defined
  decide_to_act:
    condition: decision_made AND action_plan_defined
  act_to_review:
    condition: action_executed AND review_required
  act_to_enrich:
    condition: action_executed AND NOT review_required
  review_to_enrich:
    condition: validation_completed
```

#### **Idempotência**
```yaml
# Garantias de execução segura
idempotency_rules:
  state_reentry: safe_if_postconditions_unmet
  oracle_consultation: cacheable_within_session
  enrichment: atomic_uki_creation
```

### 🚨 **Tratamento de Falhas**

#### **Comportamento em Erro**
```yaml
error_handling:
  oracle_unavailable:
    action: defer_until_available
    fallback: use_cached_ukis_if_recent
  invalid_state_transition:
    action: revert_to_last_valid_state
    log: violation_details
  enrichment_failure:
    action: mandatory_retry
    escalation: human_intervention
```

#### **Recuperação de Estado**
```yaml
recovery_patterns:
  partial_execution:
    action: resume_from_last_valid_checkpoint
  data_corruption:
    action: reconstruct_from_audit_trail
  timeout_exceeded:
    action: graceful_degradation_with_logging
```

### 📊 **Verificação de Consistência**

#### **Validações Automáticas**
```yaml
consistency_checks:
  oracle_binding:
    - motivating_ukis_exist
    - reasoning_ukis_accessible
    - enrichment_ukis_valid
  explainability:
    - signals_complete_per_state
    - decision_rationale_traceable
    - oracle_consultation_documented
  workflow_integrity:
    - all_mandatory_states_executed
    - enrichment_always_final
    - relationships_bidirectional
```

---

## 🔍 ESQUEMAS DE EXPLICABILIDADE VERIFICÁVEIS

Para garantir a qualidade e consistência dos sinais de explicabilidade, o ZWF define schemas JSON formais para validação automática dos campos `context`, `decision` e `result` em cada estado do workflow.

### 📋 **Schema Base para Sinais**

#### **Schema para Context (O que entrou)**
```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "context": {
      "type": "string",
      "pattern": "^O que entrou: .+",
      "minLength": 20,
      "maxLength": 500,
      "description": "Descrição clara e objetiva do input recebido no estado"
    }
  },
  "required": ["context"],
  "additionalProperties": false
}
```

#### **Schema para Decision (Por que transicionou)**
```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object", 
  "properties": {
    "decision": {
      "type": "string",
      "pattern": "^Por que transicionou: .+baseado.+(unik-[a-z0-9-]+).+",
      "minLength": 30,
      "maxLength": 800,
      "description": "Justificativa da transição referenciando UKIs do Oráculo"
    }
  },
  "required": ["decision"],
  "additionalProperties": false
}
```

#### **Schema para Result (O que saiu)**
```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "result": {
      "type": "string",
      "pattern": "^O que saiu: .+",
      "minLength": 15,
      "maxLength": 600,
      "description": "Descrição clara do output produzido pelo estado"
    }
  },
  "required": ["result"],
  "additionalProperties": false
}
```

### 🔗 **Schema Completo de Explicabilidade**

#### **Schema Integrado para Validação de Estado**
```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "flow_step": {
      "type": "string",
      "enum": ["intake", "understand", "decide", "act", "review", "enrich"]
    },
    "signals": {
      "type": "object",
      "properties": {
        "context": {
          "type": "string",
          "pattern": "^O que entrou: .+",
          "minLength": 20,
          "maxLength": 500
        },
        "decision": {
          "type": "string", 
          "pattern": "^Por que transicionou: .+baseado.+(unik-[a-z0-9-]+).+",
          "minLength": 30,
          "maxLength": 800
        },
        "result": {
          "type": "string",
          "pattern": "^O que saiu: .+",
          "minLength": 15,
          "maxLength": 600
        }
      },
      "required": ["context", "decision", "result"],
      "additionalProperties": false
    },
    "oracle_ukis_used": {
      "type": "array",
      "items": {
        "type": "string",
        "pattern": "^unik-[a-z0-9-]+$"
      },
      "minItems": 1,
      "uniqueItems": true
    },
    "timestamp": {
      "type": "string",
      "pattern": "^[0-9]{4}-[0-9]{2}-[0-9]{2} [0-9]{2}:[0-9]{2}:[0-9]{2}$"
    }
  },
  "required": ["flow_step", "signals", "oracle_ukis_used", "timestamp"],
  "additionalProperties": false
}
```

### ✅ **Exemplos de Validação Bem-Sucedida**

#### **Exemplo Válido - Estado Decide**
```yaml
# Input que PASSA na validação
flow_step: "decide"
signals:
  context: "O que entrou: solicitação para implementar autenticação JWT na API principal"
  decision: "Por que transicionou: escolhido padrão bearer token baseado no unik-technical-jwt-authentication-pattern que especifica melhores práticas de segurança"
  result: "O que saiu: definido usar biblioteca jsonwebtoken com configuração de expiração de 15 minutos"
oracle_ukis_used:
  - unik-technical-jwt-authentication-pattern
  - unik-business-token-expiration-policy
timestamp: "2024-01-15 14:30:22"
```

#### **Exemplo Válido - Estado Act**
```yaml
# Input que PASSA na validação
flow_step: "act"
signals:
  context: "O que entrou: plano de implementação de JWT com biblioteca jsonwebtoken aprovado"
  decision: "Por que transicionou: executada implementação baseado no unik-technical-code-standards que define estrutura de middleware"
  result: "O que saiu: middleware de autenticação implementado e testado com 100% de cobertura"
oracle_ukis_used:
  - unik-technical-code-standards
  - unik-culture-testing-requirements
timestamp: "2024-01-15 15:45:10"
```

### ❌ **Exemplos de Validação com Falha**

#### **Falha 1: Context muito curto**
```yaml
# Input que FALHA na validação
flow_step: "decide"
signals:
  context: "O que entrou: JWT"  # ERRO: menos de 20 caracteres
  decision: "Por que transicionou: baseado no unik-technical-jwt padrão de segurança"
  result: "O que saiu: biblioteca definida"
# ERRO DE VALIDAÇÃO: context deve ter mínimo 20 caracteres
```

#### **Falha 2: Decision sem referência a UKI**
```yaml
# Input que FALHA na validação
flow_step: "understand"
signals:
  context: "O que entrou: documentação de requisitos de autenticação para análise"
  decision: "Por que transicionou: analisados os requisitos e decidido prosseguir"  # ERRO: não referencia UKI
  result: "O que saiu: compreensão dos requisitos de segurança necessários"
# ERRO DE VALIDAÇÃO: decision deve conter referência a UKI (padrão "baseado.+unik-")
```

#### **Falha 3: UKI malformado**
```yaml
# Input que FALHA na validação
flow_step: "enrich"
signals:
  context: "O que entrou: implementação JWT completa para documentação"
  decision: "Por que transicionou: criado UKI baseado no unik-technical-implementation-pattern"
  result: "O que saiu: novo UKI documentando padrão de implementação JWT"
oracle_ukis_used:
  - invalid-uki-format  # ERRO: deve seguir padrão unik-[a-z0-9-]+
  - unik-technical-valid
# ERRO DE VALIDAÇÃO: UKI deve seguir formato unik-[dominio]-[identificador]
```

### 🛡️ **Uso para Auditoria e Compliance**

#### **Validação Automática em Pipelines**
```bash
# Exemplo de validação em CI/CD
jsonschema -i workflow_step.yaml zwf_explainability_schema.json
if [ $? -eq 0 ]; then
  echo "✅ Sinais de explicabilidade válidos"
else
  echo "❌ Falha na validação - workflow não conforme"
  exit 1
fi
```

#### **Métricas de Qualidade**
- **Taxa de Conformidade**: % de sinais que passam na validação
- **Rastreabilidade**: 100% das decisões devem referenciar UKIs
- **Completude**: todos os campos obrigatórios preenchidos
- **Qualidade Descritiva**: comprimentos mínimos respeitados

---

## 🎪 PADRÕES DE FLUXO (COBERTURA MÍNIMA)

### 📥 **Ingest (knowledge.added)**
```mermaid
stateDiagram-v2
    [*] --> Intake: Nova documentação
    Intake --> Understand: Organizar conteúdo
    Understand --> Decide: Consultar padrões do Oráculo
    Decide --> Act: Estruturar como UKI
    Act --> Enrich: Adicionar ao Oráculo
    Enrich --> [*]
```

### 🎫 **Request (work.proposed)**
```mermaid
stateDiagram-v2
    [*] --> Intake: Nova demanda
    Intake --> Understand: Analisar contexto
    Understand --> Decide: Consultar diretrizes
    Decide --> Act: Executar trabalho
    Act --> Review: Validação opcional
    Review --> Enrich: Documentar aprendizado
    Act --> Enrich: Documentar aprendizado
    Enrich --> [*]
```

### 🎯 **Strategy (decisão estratégica)**
```mermaid
stateDiagram-v2
    [*] --> Intake: Proposta estratégica
    Intake --> Understand: Avaliar contexto estratégico
    Understand --> Decide: Consultar políticas
    Decide --> Act: Implementar decisão
    Act --> Review: Validação stakeholders
    Review --> Enrich: Registrar decisão
    Enrich --> [*]
```

### 🔧 **Refinement (work.refine.requested)**
```mermaid
stateDiagram-v2
    [*] --> Intake: Solicitação de melhoria
    Intake --> Understand: Analisar estado atual
    Understand --> Decide: Definir melhorias
    Decide --> Act: Implementar refinamentos
    Act --> Enrich: Atualizar conhecimento
    Enrich --> [*]
```

### 🤝 **Assistance (assistance.requested)**
```mermaid
stateDiagram-v2
    [*] --> Intake: Pedido de ajuda
    Intake --> Understand: Entender problema
    Understand --> Decide: Escolher tipo de ajuda
    Decide --> Act: Prestar assistência
    Act --> Enrich: Documentar solução
    Enrich --> [*]
```

### 📝 **Feedback (feedback.submitted)**
```mermaid
stateDiagram-v2
    [*] --> Intake: Feedback recebido
    Intake --> Understand: Analisar feedback
    Understand --> Decide: Definir ações
    Decide --> Act: Implementar correções
    Act --> Enrich: Atualizar conhecimento
    Enrich --> [*]
```

---

## 🚫 LIMITES DE ZION

### ❌ **O que ZWF NÃO especifica:**
- Ferramentas específicas de implementação
- Motores de orquestração ou workflow engines
- Prompts ou interfaces de agentes
- Custos, SLAs ou métricas numéricas
- Formatos técnicos de execução
- Tecnologias de implementação

### ❌ **O que ZWF NÃO adiciona ao MEF:**
- Novos campos na estrutura UKI
- Modificações no formato YAML
- Tipos de UKI adicionais
- Apenas usa `related_to` para relacionamentos

### ✅ **O que ZWF especifica:**
- Padrão conceitual de estados de fluxo
- Tipos de eventos que iniciam workflows
- Relacionamento obrigatório com o Oráculo
- Formato de explicabilidade e rastreamento
- Estrutura de enriquecimento do conhecimento

---

## 🎯 RESULTADO ESPERADO

Com o ZWF, qualquer equipe pode:

1. **Desenhar fluxos conceituais** seguindo os estados canônicos
2. **Consultar o Oráculo** para fundamentar decisões
3. **Executar ações** usando suas próprias ferramentas
4. **Enriquecer o Oráculo** com aprendizado em formato MEF
5. **Manter rastreabilidade** através dos sinais de explicabilidade
6. **Operar orientada a IA** do discovery à entrega

**Ciclo fechado:** Consultar Oráculo → Agir → Enriquecer Oráculo

---

## 🔄 INTEGRAÇÃO COM AS CAMADAS MATRIX

### 🔮 **Relação com Oracle (MEF)**
- **Entrada:** ZWF consulta UKIs do Oráculo para fundamentar decisões
- **Saída:** ZWF produz novos UKIs MEF para enriquecer o Oráculo
- **Formato:** Todos os relacionamentos usam `related_to` do MEF

### ⚙️ **Relação com Operator**
- **ZWF → Operator:** Fornece o desenho conceitual do fluxo
- **Operator:** Implementa usando tecnologias específicas da equipe
- **ZWF:** Não prescreve como implementar, apenas o que desenhar

---

<a name="english"></a>
# English 🇺🇸

> Zion Workflow Framework

**Version:** 1.0
**Status:** Active
**Purpose:** To specify in a conceptual and standardized way the workflow framework for AI-oriented teams, defining how to describe, execute and govern workflows as technology-independent state machines.

---

## 📟️ OVERVIEW

The Matrix ZWF Protocol defines a **conceptual model for AI-oriented workflows** that allows multidisciplinary teams to describe workflows as technology-independent state machines. All flows follow the pattern: **Event → Query Oracle → Decision → Action → Oracle Enrichment**.

ZWF does not prescribe tools, orchestration engines, or technical implementations - it only directs **how to think and record the path** in a conceptual and traceable way.

---

## 🎭 ACTORS AND ROLES

### 🔮 **Oracle**
- **Function:** Strategic/semantic repository that maintains UKIs (MEF)
- **Input:** Queries for guidelines, rules, decisions, patterns and examples
- **Output:** Contextual knowledge to support flow decisions
- **Enrichment:** Receives new/updated UKIs at the end of flows

### 👥 **Teams**
- **Function:** Describe flows in ZWF conceptual language
- **Responsibility:** Implement flows using their own tools and technologies
- **Roles:** Dev/Eng/Tech/PM/UX/Analysts

### ⚙️ **Operator**
- **Function:** Executes in practice (CI/CD, IDE, orchestrators, etc.)
- **Limitation:** ZWF does not prescribe how to implement - only what to design

---

## 📡 CANONICAL EVENTS (TRIGGERS)

ZWF recognizes six types of events that initiate flows:

| Event | Description | Typical Context |
|--------|-------------|-----------------|
| `knowledge.added` | New content available | Documentation, specifications, decisions |
| `work.proposed` | New work proposal | Story, epic, feature, strategy |
| `work.refine.requested` | Refinement request | Improvements, adjustments, optimizations |
| `assistance.requested` | Help/collaboration request | Pair programming, consulting, support |
| `test.authored` | Test scenarios created | Unit tests, integration, acceptance |
| `feedback.submitted` | Correction/learning | Bug reports, improvements, lessons learned |

---

## 🔄 CANONICAL STATES (STATE MACHINE)

Every ZWF flow follows this mandatory conceptual sequence:

```mermaid
stateDiagram-v2
    [*] --> Intake
    Intake --> Understand
    Understand --> Decide
    Decide --> Act
    Act --> Review
    Act --> Enrich
    Review --> Enrich
    Enrich --> [*]
    
    note right of Understand
      Query Oracle UKIs
      for interpretation
    end note
    
    note right of Review
      Optional state
      Human intervention
    end note
    
    note right of Enrich
      Mandatory
      Return learning
      as MEF UKIs
    end note
```

### 📨 **Intake**
- **Purpose:** Receive the event and organize the context
- **Actions:** Capture event data, validate format, prepare context
- **Output:** Structured context for Oracle consultation

### 🧠 **Understand (via Oracle)**
- **Purpose:** Query relevant UKIs to interpret intention/risk/context
- **Actions:** Semantic search in Oracle, analysis of related UKIs
- **Output:** Contextual knowledge to support decisions

### ⚖️ **Decide**
- **Purpose:** Choose path based on Oracle guidelines
- **Actions:** Apply business rules, assess risks, define actions
- **Output:** Action plan based on UKIs

### 🎯 **Act**
- **Purpose:** Execute action with people, agents or tools
- **Actions:** Practical implementation using team's available resources
- **Output:** Execution result + learning context

### 👁️ **Review (Optional)**
- **Purpose:** Human intervention when necessary
- **Actions:** Human validation, approval, adjustments
- **Output:** Confirmation or redirection

### 🔄 **Enrich Oracle (Mandatory)**
- **Purpose:** Return learning as valid MEF UKIs
- **Actions:** Create/update UKIs referential to what motivated the flow
- **Output:** Structured knowledge added to Oracle

---

## 🔗 ORACLE BINDING

### 📋 **Initial Declaration**
Every flow must declare at the beginning which Oracle UKIs motivate it:

```yaml
# Example of flow declaration
flow_id: zion-workflow-jwt-implementation
triggered_by: work.proposed
oracle_context:
  motivating_ukis:
    - unik-technical-jwt-authentication-pattern
    - unik-business-security-requirements
    - unik-culture-code-review-process
```

### ⚖️ **Decision Foundation**
During transitions, the flow must explicitly state which UKIs support each decision:

```yaml
# Example of founded decision
decision_point: "choose_jwt_library"
reasoning_ukis:
  - unik-technical-jwt-security-standards
  - unik-business-vendor-approval-policy
decision_outcome: "use_jsonwebtoken_library"
```

### 🔄 **Mandatory Enrichment**
Outputs must reference motivating UKIs through the `related_to` field:

```yaml
# Example of UKI generated in enrichment
id: unik-technical-jwt-implementation-result
related_to:
  - unik-technical-jwt-authentication-pattern  # Motivating UKI
  - unik-business-security-requirements        # Motivating UKI
content: |
  Successful JWT pattern implementation following security guidelines.
  Based on related UKIs guidance, adapted to our specific context.
```

---

## 📤 MANDATORY OUTPUTS

### 🎯 **MEF Output Types**
Every flow must return something to Oracle choosing among MEF types:

| UKI Type | When to Use | Example Output |
|----------|-------------|----------------|
| `business_rule` | Established rule | New authentication policy |
| `guideline` | Consolidated guideline | Updated code review process |
| `pattern` | Standardized practice | API implementation pattern |
| `decision` | Registered decision | Documented technology choice |
| `template` | Reusable template | Configuration template |
| `function` | Specific implementation | JWT validation function |
| `example` | Documented use case | API usage example |

### 🔗 **Mandatory Relationships**
Each generated UKI must include:
- `related_to`: UKIs that motivated/impacted the flow
- Clear summary of relationship intention in `content` field

---

## 📊 MINIMAL EXPLAINABILITY

In each flow state, record three signals in natural language:

### 📝 **Recording Template**
```yaml
flow_step: [state_name]
signals:
  context: "What came in: [input description]"
  decision: "Why it transitioned: [justification based on Oracle UKIs]"
  result: "What came out: [output description]"
oracle_ukis_used:
  - unik-[consulted-uki-id]
timestamp: [YYYY-MM-DD HH:MM:SS]
```

### 💡 **Practical Example**
```yaml
flow_step: "decide"
signals:
  context: "Received request to implement JWT authentication in API"
  decision: "Chosen bearer token pattern based on unik-technical-jwt-authentication-pattern specifying security best practices"
  result: "Defined to use jsonwebtoken library with 15-minute expiration configuration"
oracle_ukis_used:
  - unik-technical-jwt-authentication-pattern
  - unik-business-token-expiration-policy
timestamp: "2024-01-15 14:30:22"
```

---

## 📊 CANONICAL TELEMETRY METRICS

For effective observability and monitoring of ZWF workflows, we establish standardized metrics that should be collected during the execution of each flow.

### 🕘 **State Transition Duration Metrics**
```yaml
state_transition_duration:
  intake_to_understand: 
    timestamp_start: "2024-01-15T14:30:22Z"
    timestamp_end: "2024-01-15T14:32:15Z"
    duration_seconds: 113
  understand_to_decide:
    timestamp_start: "2024-01-15T14:32:15Z"
    timestamp_end: "2024-01-15T14:35:48Z"
    duration_seconds: 213
  decide_to_act:
    timestamp_start: "2024-01-15T14:35:48Z"
    timestamp_end: "2024-01-15T14:45:30Z"
    duration_seconds: 582
  act_to_review:
    timestamp_start: "2024-01-15T14:45:30Z"
    timestamp_end: "2024-01-15T14:48:12Z"
    duration_seconds: 162
  review_to_enrich:
    timestamp_start: "2024-01-15T14:48:12Z"
    timestamp_end: "2024-01-15T14:50:05Z"
    duration_seconds: 113
```

### 📈 **Transition Quality Metrics**
```yaml
transition_quality_score:
  overall_workflow_score: 85  # 0-100
  state_scores:
    intake: 90     # Context capture completeness
    understand: 88 # Oracle consultation quality
    decide: 82     # Decision foundation strength
    act: 85        # Execution effectiveness
    review: 95     # Validation quality
    enrich: 78     # Generated UKI quality
  quality_factors:
    oracle_coverage: 85      # % of decisions founded on UKIs
    explainability_depth: 90 # Signal detail level
    relationship_clarity: 80 # related_to clarity
```

### 🏥 **Workflow Health Metrics**
```yaml
workflow_health_metrics:
  completion_status: "successful"  # successful | failed | partial
  error_count: 0
  warning_count: 2
  retry_count: 1
  state_coverage: 
    total_states: 6
    executed_states: 6
    skipped_states: 0
  oracle_availability: "available"  # available | degraded | unavailable
  enrichment_success: true
```

### 🔮 **Oracle Enrichment Efficiency Metrics**
```yaml
oracle_enrichment_metrics:
  ukis_consulted: 5
  ukis_created: 1
  ukis_updated: 0
  relationship_count: 3
  knowledge_domains_touched:
    - technical
    - business
  semantic_coherence_score: 87  # 0-100
  reusability_potential: "high"  # low | medium | high
```

### 📋 **Complete Metrics Template**
```yaml
telemetry:
  workflow_id: "zwf-jwt-implementation-001"
  execution_start: "2024-01-15T14:30:22Z"
  execution_end: "2024-01-15T14:50:05Z"
  total_duration_seconds: 1183
  
  state_transition_duration: [structure above]
  transition_quality_score: [structure above]
  workflow_health_metrics: [structure above]
  oracle_enrichment_metrics: [structure above]
  
  performance_indicators:
    throughput_score: 85        # Speed vs. quality balance
    efficiency_ratio: 0.73      # Useful time / total time
    oracle_hit_rate: 0.89       # UKIs found / UKIs searched
    decision_confidence: 0.85   # Confidence in decisions made
  
  observability_tags:
    team: "backend-squad"
    trigger_type: "work.proposed"
    complexity_level: "medium"   # low | medium | high
    ai_assistance_level: "high"  # none | low | medium | high
```

---

## ⚖️ STATE INVARIANTS (FORMAL)

To ensure robust and deterministic execution, each ZWF state must meet conceptual invariants that can be implemented by durable engines:

### 📋 **Invariants per State**

#### 📨 **Intake State**
```yaml
preconditions:
  - trigger_event: defined
  - event_type: valid_canonical_event
postconditions:
  - context_structured: true
  - trigger_validated: true
  - oracle_context_prepared: true
validation:
  required_fields: [flow_id, triggered_by, oracle_context]
  context_format: structured
```

#### 🧠 **Understand State**
```yaml
preconditions:
  - intake_completed: true
  - context_structured: true
postconditions:
  - oracle_consulted: true
  - ukis_identified: min_1
  - strategy_defined: true
validation:
  required_ukis: min_1
  oracle_response: structured
  understanding_documented: true
```

#### ⚖️ **Decide State**
```yaml
preconditions:
  - understanding_completed: true
  - oracle_knowledge_available: true
postconditions:
  - decision_made: true
  - reasoning_documented: true
  - action_plan_defined: true
validation:
  decision_rationale: required
  reasoning_ukis: min_1
  action_plan: structured
```

#### 🎯 **Act State**
```yaml
preconditions:
  - decision_made: true
  - action_plan_defined: true
postconditions:
  - action_executed: true
  - execution_result: documented
  - learning_context_captured: true
validation:
  execution_evidence: required
  result_documentation: structured
  error_handling: documented
```

#### 👁️ **Review State (Optional)**
```yaml
preconditions:
  - action_executed: true
  - review_required: true
postconditions:
  - validation_completed: true
  - approval_status: defined
  - feedback_documented: true
validation:
  review_criteria: defined
  reviewer_input: documented
  outcome_clear: true
```

#### 🔄 **Enrich State (Mandatory)**
```yaml
preconditions:
  - workflow_completed: true
  - learning_captured: true
postconditions:
  - uki_created: true
  - oracle_updated: true
  - relationships_established: true
validation:
  uki_format: mef_compliant
  related_to: motivating_ukis_referenced
  content_meaningful: true
```

### 🔄 **Transition Invariants**

#### **State to State**
```yaml
# General transition rules
transition_rules:
  intake_to_understand:
    condition: context_structured AND oracle_context_prepared
  understand_to_decide:
    condition: oracle_consulted AND strategy_defined
  decide_to_act:
    condition: decision_made AND action_plan_defined
  act_to_review:
    condition: action_executed AND review_required
  act_to_enrich:
    condition: action_executed AND NOT review_required
  review_to_enrich:
    condition: validation_completed
```

#### **Idempotency**
```yaml
# Safe execution guarantees
idempotency_rules:
  state_reentry: safe_if_postconditions_unmet
  oracle_consultation: cacheable_within_session
  enrichment: atomic_uki_creation
```

### 🚨 **Failure Handling**

#### **Error Behavior**
```yaml
error_handling:
  oracle_unavailable:
    action: defer_until_available
    fallback: use_cached_ukis_if_recent
  invalid_state_transition:
    action: revert_to_last_valid_state
    log: violation_details
  enrichment_failure:
    action: mandatory_retry
    escalation: human_intervention
```

#### **State Recovery**
```yaml
recovery_patterns:
  partial_execution:
    action: resume_from_last_valid_checkpoint
  data_corruption:
    action: reconstruct_from_audit_trail
  timeout_exceeded:
    action: graceful_degradation_with_logging
```

### 📊 **Consistency Verification**

#### **Automatic Validations**
```yaml
consistency_checks:
  oracle_binding:
    - motivating_ukis_exist
    - reasoning_ukis_accessible
    - enrichment_ukis_valid
  explainability:
    - signals_complete_per_state
    - decision_rationale_traceable
    - oracle_consultation_documented
  workflow_integrity:
    - all_mandatory_states_executed
    - enrichment_always_final
    - relationships_bidirectional
```

---

## 🔍 VERIFIABLE EXPLAINABILITY SCHEMAS

To ensure quality and consistency of explainability signals, ZWF defines formal JSON schemas for automatic validation of `context`, `decision` and `result` fields in each workflow state.

### 📋 **Base Schemas for Signals**

#### **Schema for Context (What came in)**
```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "context": {
      "type": "string",
      "pattern": "^What came in: .+",
      "minLength": 20,
      "maxLength": 500,
      "description": "Clear and objective description of the input received in the state"
    }
  },
  "required": ["context"],
  "additionalProperties": false
}
```

#### **Schema for Decision (Why it transitioned)**
```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object", 
  "properties": {
    "decision": {
      "type": "string",
      "pattern": "^Why it transitioned: .+based.+(unik-[a-z0-9-]+).+",
      "minLength": 30,
      "maxLength": 800,
      "description": "Transition justification referencing Oracle UKIs"
    }
  },
  "required": ["decision"],
  "additionalProperties": false
}
```

#### **Schema for Result (What came out)**
```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "result": {
      "type": "string",
      "pattern": "^What came out: .+",
      "minLength": 15,
      "maxLength": 600,
      "description": "Clear description of the output produced by the state"
    }
  },
  "required": ["result"],
  "additionalProperties": false
}
```

### 🔗 **Complete Explainability Schema**

#### **Integrated Schema for State Validation**
```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "flow_step": {
      "type": "string",
      "enum": ["intake", "understand", "decide", "act", "review", "enrich"]
    },
    "signals": {
      "type": "object",
      "properties": {
        "context": {
          "type": "string",
          "pattern": "^What came in: .+",
          "minLength": 20,
          "maxLength": 500
        },
        "decision": {
          "type": "string", 
          "pattern": "^Why it transitioned: .+based.+(unik-[a-z0-9-]+).+",
          "minLength": 30,
          "maxLength": 800
        },
        "result": {
          "type": "string",
          "pattern": "^What came out: .+",
          "minLength": 15,
          "maxLength": 600
        }
      },
      "required": ["context", "decision", "result"],
      "additionalProperties": false
    },
    "oracle_ukis_used": {
      "type": "array",
      "items": {
        "type": "string",
        "pattern": "^unik-[a-z0-9-]+$"
      },
      "minItems": 1,
      "uniqueItems": true
    },
    "timestamp": {
      "type": "string",
      "pattern": "^[0-9]{4}-[0-9]{2}-[0-9]{2} [0-9]{2}:[0-9]{2}:[0-9]{2}$"
    }
  },
  "required": ["flow_step", "signals", "oracle_ukis_used", "timestamp"],
  "additionalProperties": false
}
```

### ✅ **Successful Validation Examples**

#### **Valid Example - Decide State**
```yaml
# Input that PASSES validation
flow_step: "decide"
signals:
  context: "What came in: request to implement JWT authentication in the main API"
  decision: "Why it transitioned: chosen bearer token pattern based on unik-technical-jwt-authentication-pattern specifying security best practices"
  result: "What came out: defined to use jsonwebtoken library with 15-minute expiration configuration"
oracle_ukis_used:
  - unik-technical-jwt-authentication-pattern
  - unik-business-token-expiration-policy
timestamp: "2024-01-15 14:30:22"
```

#### **Valid Example - Act State**
```yaml
# Input that PASSES validation
flow_step: "act"
signals:
  context: "What came in: JWT implementation plan with jsonwebtoken library approved"
  decision: "Why it transitioned: executed implementation based on unik-technical-code-standards defining middleware structure"
  result: "What came out: authentication middleware implemented and tested with 100% coverage"
oracle_ukis_used:
  - unik-technical-code-standards
  - unik-culture-testing-requirements
timestamp: "2024-01-15 15:45:10"
```

### ❌ **Validation Failure Examples**

#### **Failure 1: Context too short**
```yaml
# Input that FAILS validation
flow_step: "decide"
signals:
  context: "What came in: JWT"  # ERROR: less than 20 characters
  decision: "Why it transitioned: based on unik-technical-jwt security pattern"
  result: "What came out: library defined"
# VALIDATION ERROR: context must have minimum 20 characters
```

#### **Failure 2: Decision without UKI reference**
```yaml
# Input that FAILS validation
flow_step: "understand"
signals:
  context: "What came in: authentication requirements documentation for analysis"
  decision: "Why it transitioned: analyzed requirements and decided to proceed"  # ERROR: no UKI reference
  result: "What came out: understanding of necessary security requirements"
# VALIDATION ERROR: decision must contain UKI reference (pattern "based.+unik-")
```

#### **Failure 3: Malformed UKI**
```yaml
# Input that FAILS validation
flow_step: "enrich"
signals:
  context: "What came in: complete JWT implementation for documentation"
  decision: "Why it transitioned: created UKI based on unik-technical-implementation-pattern"
  result: "What came out: new UKI documenting JWT implementation pattern"
oracle_ukis_used:
  - invalid-uki-format  # ERROR: must follow unik-[a-z0-9-]+ pattern
  - unik-technical-valid
# VALIDATION ERROR: UKI must follow unik-[domain]-[identifier] format
```

### 🛡️ **Usage for Audit and Compliance**

#### **Automatic Validation in Pipelines**
```bash
# Example validation in CI/CD
jsonschema -i workflow_step.yaml zwf_explainability_schema.json
if [ $? -eq 0 ]; then
  echo "✅ Valid explainability signals"
else
  echo "❌ Validation failed - non-compliant workflow"
  exit 1
fi
```

#### **Quality Metrics**
- **Compliance Rate**: % of signals that pass validation
- **Traceability**: 100% of decisions must reference UKIs
- **Completeness**: all required fields filled
- **Descriptive Quality**: minimum lengths respected

---

## 🎪 FLOW PATTERNS (MINIMAL COVERAGE)

### 📥 **Ingest (knowledge.added)**
```mermaid
stateDiagram-v2
    [*] --> Intake: New documentation
    Intake --> Understand: Organize content
    Understand --> Decide: Query Oracle patterns
    Decide --> Act: Structure as UKI
    Act --> Enrich: Add to Oracle
    Enrich --> [*]
```

### 🎫 **Request (work.proposed)**
```mermaid
stateDiagram-v2
    [*] --> Intake: New demand
    Intake --> Understand: Analyze context
    Understand --> Decide: Query guidelines
    Decide --> Act: Execute work
    Act --> Review: Optional validation
    Review --> Enrich: Document learning
    Act --> Enrich: Document learning
    Enrich --> [*]
```

### 🎯 **Strategy (strategic decision)**
```mermaid
stateDiagram-v2
    [*] --> Intake: Strategic proposal
    Intake --> Understand: Assess strategic context
    Understand --> Decide: Query policies
    Decide --> Act: Implement decision
    Act --> Review: Stakeholder validation
    Review --> Enrich: Register decision
    Enrich --> [*]
```

### 🔧 **Refinement (work.refine.requested)**
```mermaid
stateDiagram-v2
    [*] --> Intake: Improvement request
    Intake --> Understand: Analyze current state
    Understand --> Decide: Define improvements
    Decide --> Act: Implement refinements
    Act --> Enrich: Update knowledge
    Enrich --> [*]
```

### 🤝 **Assistance (assistance.requested)**
```mermaid
stateDiagram-v2
    [*] --> Intake: Help request
    Intake --> Understand: Understand problem
    Understand --> Decide: Choose help type
    Decide --> Act: Provide assistance
    Act --> Enrich: Document solution
    Enrich --> [*]
```

### 📝 **Feedback (feedback.submitted)**
```mermaid
stateDiagram-v2
    [*] --> Intake: Feedback received
    Intake --> Understand: Analyze feedback
    Understand --> Decide: Define actions
    Decide --> Act: Implement corrections
    Act --> Enrich: Update knowledge
    Enrich --> [*]
```

---

## 🚫 ZION BOUNDARIES

### ❌ **What ZWF does NOT specify:**
- Specific implementation tools
- Orchestration engines or workflow engines
- Agent prompts or interfaces
- Costs, SLAs or numerical metrics
- Technical execution formats
- Implementation technologies

### ❌ **What ZWF does NOT add to MEF:**
- New fields in UKI structure
- YAML format modifications
- Additional UKI types
- Only uses `related_to` for relationships

### ✅ **What ZWF specifies:**
- Conceptual pattern of flow states
- Types of events that initiate workflows
- Mandatory relationship with Oracle
- Explainability and tracking format
- Knowledge enrichment structure

---

## 🎯 EXPECTED RESULT

With ZWF, any team can:

1. **Design conceptual flows** following canonical states
2. **Query Oracle** to support decisions
3. **Execute actions** using their own tools
4. **Enrich Oracle** with learning in MEF format
5. **Maintain traceability** through explainability signals
6. **Operate AI-oriented** from discovery to delivery

**Closed loop:** Query Oracle → Act → Enrich Oracle

---

## 🔄 INTEGRATION WITH MATRIX LAYERS

### 🔮 **Relationship with Oracle (MEF)**
- **Input:** ZWF queries Oracle UKIs to support decisions
- **Output:** ZWF produces new MEF UKIs to enrich Oracle
- **Format:** All relationships use MEF's `related_to`

### ⚙️ **Relationship with Operator**
- **ZWF → Operator:** Provides conceptual flow design
- **Operator:** Implements using team-specific technologies
- **ZWF:** Does not prescribe how to implement, only what to design