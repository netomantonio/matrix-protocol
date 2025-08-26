# ZOF — Zion Orchestration Framework
**Acrônimo:** ZOF  
**Status:** Ativo  
**Versão:** 1.0.0  
**Data:** 2025-01-25  

> ⚠️ **IMPORTANTE**: Este documento é uma tradução informativa. A versão autoritativa é [ZOF_ZION_ORCHESTRATION_FRAMEWORK.md](ZOF_ZION_ORCHESTRATION_FRAMEWORK.md).

> 🚨 **AVISO IMPORTANTE**: Este documento contém EXEMPLOS ILUSTRATIVOS (como `strategy`, `operations`, etc.) que NÃO são taxonomias obrigatórias. O **MOC (Matrix Ontology Catalog)** é a única fonte definitiva para taxonomias organizacionais.

---

## 1. Introdução

O **Zion Orchestration Framework (ZOF)** especifica de forma conceitual e padronizada o framework de fluxos de trabalho para equipes orientadas a IA, definindo como descrever, executar e governar workflows como máquinas de estado independentes de tecnologia.

O ZOF define um **modelo conceitual para fluxos de trabalho orientados a IA** que permite que equipes multidisciplinares descrevam workflows como máquinas de estado independentes de tecnologia seguindo o padrão: **Evento → Consulta Oráculo → Decisão → Ação → Avaliação → Enriquecimento Condicional do Oráculo**.

O ZOF não prescreve ferramentas, motores de orquestração ou implementações técnicas - apenas direciona **como pensar e registrar o caminho** de forma conceitual, rastreável e governada.

---

## 2. Termos e Definições

- **Estados Canônicos**: Sequência universal de estados em workflows (Intake → Understand → Decide → Act → EvaluateForEnrich → Review → Enrich)
- **EvaluateForEnrich**: Checkpoint obrigatório para avaliação de enriquecimento
- **Eventos Canônicos**: Gatilhos padrão para workflows (knowledge.added, work.proposed, etc.)
- **Sinais de Explicabilidade**: Contexto, decisão e resultado registrados em cada estado
- **can_enrich?()**: Função de filtro cognitivo para decisão de enriquecimento

Referências adicionais no **MOC (Matrix Ontology Catalog)** para taxonomias organizacionais específicas.

---

## 3. Conceitos Centrais

### Essência do ZOF em 3 Conceitos

**1. Fluxo Pensado como Estado**
- Todo trabalho é uma jornada: Recebo → Entendo → Decido → Faço → Avalio → (Possivelmente) Ensino
- Cada transição é consciente: sei por que mudei de estado
- Explicabilidade é natural: registro contexto, decisão e resultado

**2. Oracle como Conselheiro Inteligente**
- Antes de decidir qualquer coisa, consulto o Oracle: "O que já sabemos sobre isso?"
- Oracle me retorna apenas conhecimento que tenho autoridade para ver (via MOC)
- No final, posso ensinar o Oracle se aprendi algo verdadeiramente novo

**3. Governança via MOC (Matrix Ontology Catalog)**
- MOC define quem pode criar conhecimento em qual escopo/domínio
- MOC estabelece critérios organizacionais para validar se vale a pena ensinar o Oracle
- Diferentes organizações configuram diferentes regras - não há imposições globais

### O Padrão Universal
```
EVENTO → CONSULTA ORACLE → DECISÃO → AÇÃO → AVALIO SE VALE ENSINAR → (ENSINO)
```

### Estados Canônicos Obrigatórios
Todo fluxo ZOF segue esta sequência conceitual:
1. **Intake**: Captura de contexto e requisitos
2. **Understand**: Consulta obrigatória ao Oráculo (UKIs)
3. **Decide**: Decisão baseada em conhecimento existente
4. **Act**: Execução da ação planejada
5. **EvaluateForEnrich**: Checkpoint obrigatório de avaliação
6. **Review**: Validação opcional do resultado
7. **Enrich**: Enriquecimento condicional do Oráculo

---

## 4. Regras Normativas

> ⚠️ Esta seção é **normativa**.

### Estados Canônicos Obrigatórios
Todos os workflows ZOF DEVEM seguir a sequência de estados canônicos sem exceção.

### Checkpoint EvaluateForEnrich Obrigatório
- DEVE ser aplicado em todos os workflows
- DEVE consultar critérios definidos no MOC organizacional
- DEVE gerar justificativa epistemológica para decisões
- DEVE respeitar autoridades e escopos do MOC
- DEVE detectar tipos de conflito H1/H2/H3 e invocar MAL se resolução local falhar
- DEVE aplicar decisões MAL quando arbitragem for necessária

### Sinais de Explicabilidade Obrigatórios
Cada transição de estado DEVE registrar:
- **context**: O que entrou no estado
- **decision**: Por que transicionou
- **result**: O que saiu do estado

### Consulta Oracle Obrigatória
O estado **Understand** DEVE sempre consultar o Oracle (UKIs) antes de qualquer decisão.

---

## 5. Interoperabilidade

- **MEF (Matrix Embedding Framework)**: Fornece estrutura UKI consumida e produzida pelos workflows; persiste Decision Records MAL
- **MOC (Matrix Ontology Catalog)**: Define taxonomias e critérios para checkpoint EvaluateForEnrich; configura políticas de arbitragem MAL
- **OIF (Operator Intelligence Framework)**: Implementa arquétipos que executam workflows ZOF; explica resultados de arbitragem MAL aos usuários
- **MEP (Matrix Epistemic Principle)**: Estabelece fundamentos epistemológicos para enriquecimento; fornece base para justificativas epistêmicas MAL
- **MAL (Matrix Arbiter Layer)**: Invocada pelo ZOF quando EvaluateForEnrich detecta conflitos não resolúveis (H1/H2/H3); fornece decisões de arbitragem determinística; retorna ações para execução ZOF (gate_enrich, deprecate, partition_scope)

---

## 6. Convenções e Exemplos

Todos os exemplos neste documento são **meramente ilustrativos** e não definem comportamento normativo.  
A semântica normativa (escopos, governança, arquétipos, critérios de enriquecimento) é sempre derivada do **MOC (Matrix Ontology Catalog)** de cada organização.  
Os exemplos são fornecidos para fins de clareza e PODEM ser adaptados aos contextos locais, mas NÃO DEVEM ser tratados como obrigações no nível do protocolo.

---

## 7. Exemplos Ilustrativos (Apêndice)

> **Exemplo (Informativo, Dependente do MOC)**

### **Estados Canônicos com Sinais**
```yaml
# --- Exemplo Ilustrativo ---
flow_execution:
  - state: "intake"
    signals:
      context: "História de usuário para autenticação JWT recebida"
      decision: "História clara e completa, prosseguir para entendimento"
      result: "Requisitos organizados e contexto capturado"
  
  - state: "understand"
    signals:
      context: "Consultar Oracle sobre padrões de autenticação existentes"
      decision: "UKI uki:technical:pattern:jwt-authentication encontrada"
      result: "Conhecimento existente identificado e compreendido"
  
  - state: "decide"
    signals:
      context: "Baseado em UKI existente, decidir abordagem de implementação"
      decision: "Usar biblioteca recomendada conforme padrão organizacional"
      result: "Estratégia de implementação definida"
```

### **Checkpoint EvaluateForEnrich**
```yaml
# --- Exemplo Ilustrativo ---
evaluate_for_enrich:
  checkpoint_execution:
    - state: "evaluate_for_enrich"
      signals:
        context: "Implementação JWT concluída com adaptações para contexto"
        decision: "can_enrich?(resultado, contexto, critérios_MOC) = APROVADO"
        result: "Conhecimento qualifica para enriquecimento escopo 'team'"
  
  moc_criteria_applied:
    - criterion: "relevance"
      threshold: "medium"
      evaluation: "PASS - outros desenvolvedores enfrentarão mesmo problema"
    - criterion: "reusability"
      threshold: "high"
      evaluation: "PASS - solução pode ser reutilizada em outros projetos"
```

### **Perfil Mínimo can_enrich?() - Adoção Inicial**
```yaml
# --- Exemplo Ilustrativo ---
# Para organizações iniciando com ZOF, função simplificada com 3 perguntas básicas
minimum_can_enrich_profile:
  
  # 1. NOVIDADE: Há algo novo aqui?
  semantic_novelty:
    question: "Aprendi algo que não existia antes na nossa base de conhecimento?"
    examples_yes:
      - "Descobri uma nova forma de resolver X"
      - "Identifiquei um padrão que não estava documentado"
    examples_no:
      - "Apenas executei um processo já conhecido"
      - "Deploy/build rotineiro sem descobertas"
  
  # 2. UTILIDADE: Vale a pena para outros?
  practical_value:
    question: "Outros na minha equipe se beneficiariam desse conhecimento?"
    examples_yes:
      - "Outros desenvolvedores enfrentarão este problema"
      - "Esta abordagem economiza tempo significativo"
    examples_no:
      - "É específico da minha situação particular"
      - "Informação que todos já sabem"
  
  # 3. AUTORIDADE: Posso criar conhecimento neste escopo?
  basic_authority:
    question: "Tenho autoridade para criar conhecimento neste domínio?"
    simple_check: |
      if (uki_proposal.scope_ref == "team" && 
          user_context.domains.includes(uki_proposal.domain_ref)):
        return AUTHORIZED
      else:
        return REQUIRES_APPROVAL
```

### **Eventos Canônicos**
```yaml
# --- Exemplo Ilustrativo ---
canonical_events:
  knowledge.added: "Novo conteúdo disponível"
  work.proposed: "Nova proposta de trabalho"
  work.refine.requested: "Solicitação de refinamento"
  assistance.requested: "Pedido de ajuda/colaboração"
  test.authored: "Cenários de teste criados"
  feedback.submitted: "Correção/aprendizado"

workflow_patterns:
  request_flow: "Implementação de nova funcionalidade"
  refinement_flow: "Otimização de processo existente"
  ingestion_flow: "Processamento de documentação externa"
  assistance_flow: "Suporte técnico estruturado"
  testing_flow: "Criação de cenários de teste"
  feedback_flow: "Processamento de correções"
```

### **Implementação Livre**
```yaml
# --- Exemplo Ilustrativo ---
zof_prescribes:
  how_to_think: "Como estruturar o pensamento do fluxo"
  when_to_consult: "Quando consultar o Oracle"
  how_to_evaluate: "Como avaliar se vale ensinar algo novo"
  how_to_record: "Como registrar explicabilidade das decisões"

zof_does_not_prescribe:
  which_tools: "Qual ferramenta usar (Jira, GitHub, Slack, etc.)"
  how_to_implement: "Como implementar tecnicamente"
  which_metrics: "Quais métricas coletar"
  how_to_deploy: "Como fazer deploy"

benefits:
  consistency: "Mesma forma de pensar, diferentes ferramentas"
  traceability: "Sei sempre por que tomei cada decisão"
  evolution: "Conhecimento organizacional cresce de forma governada"
  flexibility: "Cada equipe implementa com suas tecnologias"
  authority: "Respeitamos hierarquias organizacionais via MOC"
```

---

## 8. Referências Cruzadas

- [MEF — Matrix Embedding Framework](MEF_MATRIX_EMBEDDING_FRAMEWORK.md)  
- [MOC — Matrix Ontology Catalog](MOC_MATRIX_ONTOLOGY_CATALOG.md)  
- [OIF — Operator Intelligence Framework](OIF_OPERATOR_INTELLIGENCE_FRAMEWORK.md)  
- [MEP — Matrix Epistemic Principle](MEP_MATRIX_EPISTEMIC_PRINCIPLE.md)  
- [MAL — Matrix Arbiter Layer](MAL_MATRIX_ARBITER_LAYER.md)  