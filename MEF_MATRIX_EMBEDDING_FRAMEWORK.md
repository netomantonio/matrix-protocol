# 📜 MATRIX MEF PROTOCOL | PROTOCOLO MATRIX MEF


## 🌎 Idioma / Language

- [Português 🇧🇷](#português)
- [English 🇺🇸](#english)

---

<a name="português"></a>
# Português 🇧🇷

> Matrix Embedding Framework

**Versão:** 1.0
**Status:** Ativo
**Finalidade:** Especificar de forma integral, padronizada e internacionalizada a estrutura mínima e completa de conhecimento embebido versionado a ser utilizada por pessoas e agentes inteligentes no contexto do Protocolo Matrix.

---

## 📟️ VISÃO GERAL

O Protocolo Matrix MEF define um **modelo padronizado de estruturação do conhecimento versionado** que permite que qualquer membro de um time multidisciplinar (desenvolvedores, PMs, analistas, tech leads etc.) possa criar, registrar, interligar e utilizar unidades mínimas de conhecimento — chamadas de **UKIs (Units of Knowledge Interlinked)**.

Essas unidades são embebidas e consumidas por agentes inteligentes, garantindo rastreabilidade, aplicabilidade, evolução controlada e inteligência contextual em tempo real.

### 🏛️ **Integração com MOC (Matrix Ontology Catalog)**

O MEF utiliza o **MOC como fonte única de taxonomias organizacionais**:
- **Campos *_ref**: Todos os campos hierárquicos (scope_ref, domain_ref, type_ref, maturity_ref) fazem referência a nós definidos no MOC organizacional
- **Flexibilidade Local**: Organizações configuram suas próprias hierarquias mantendo estrutura universal MEF
- **Governança Integrada**: MOC define regras de autoridade e visibilidade que o MEF respeita durante criação e consulta de UKIs
- **Documento de Referência**: Ver especificação completa em `MOC_MATRIX_ONTOLOGY_CATALOG.md`

### 🧭 **Orientação Epistemológica (MEP)**

O MEF implementa os princípios epistemológicos estabelecidos pelo **Matrix Epistemic Principle (MEP)**:
- **Estratificação**: Campo `maturity_ref` reflete níveis epistemológicos (draft → validated → approved)
- **Promoção Responsável**: Campo `promotion_rationale` documenta justificativas para evolução de conhecimento
- **Autoridade Derivada**: Campos `scope_ref` e `governance_ref` implementam autoridade contextual e relativa
- **Documento de Referência**: Ver manifesto completo em `MEP_MATRIX_EPISTEMIC_PRINCIPLE.md`

---

# 🔧 ESTRUTURA PADRÃO DE UMA UKI

## 📌 Formato: **YAML estruturado**

Cada arquivo representa uma **única UKI**.

```yaml

schema: "1.0"
ontology_reference: "Ontology_MEF_Support v1.0"
version: "[MAJOR.MINOR.PATCH]"

id: uki:[domain_ref]:[type_ref]:[slug_or_id]
title: [Título objetivo e descritivo da unidade]
scope_ref: [Referência ao nó de escopo no MOC]
scope_mode: [restricted | propagated]  # Modo de propagação do escopo
domain_ref: [Referência ao nó de domínio no MOC]
type_ref: [Referência ao nó de tipo no MOC]
context_ref: [Referência ao nó de contexto no MOC]  # Opcional se definido no MOC
maturity_ref: [Referência ao nó de maturidade no MOC]  # Controla validação e confiabilidade
created_date: [YYYY-MM-DD]  # Data de criação da primeira versão
last_modified: [YYYY-MM-DD]  # Data da última modificação
change_summary: [Resumo das mudanças na versão atual]  # Opcional para versão inicial
change_impact: [major | minor | patch]  # Tipo de impacto da mudança
previous_version: "[MAJOR.MINOR.PATCH]"  # Versão anterior (opcional para versão inicial)

status: [active | deprecated | archived]  # OBRIGATÓRIO: controle de ciclo de vida

domain_of_influence: [referência_ao_moc_organizational]  # RECOMENDADO: área de impacto configurada via MOC

# 🚨 AVISO: EXEMPLOS NÃO SÃO TAXONOMIA OBRIGATÓRIA
# Os valores mostrados anteriormente (strategy, operations, etc.) são APENAS EXEMPLOS ILUSTRATIVOS.
# Cada organização define seus domínios de influência no MOC.
# 🏛️ MOC é a única fonte de taxonomias válidas.

relationships:  # OBRIGATÓRIO: ontologia formal com tipos padronizados
  - type: [depends_on | overrides | conflicts_with | complements | amends | precedes | equivalent_to]
    target: uki:[domain]:[type]:[identifier]
    description: [Descrição específica da relação ontológica]

promotion:  # OPCIONAL: campos para promoção de UKI
  is_promoted_from: uki:[domain]:[type]:[identifier]  # UKI de origem quando for promoção
  promotion_rationale: [Justificativa da promoção]  # Motivos e evidências para elevação

impact_analysis:  # OPCIONAL: análise de cadeia de impacto
  chain_preview:
    - uki:domain:type:item-a → uki:domain:type:item-b → uki:domain:type:item-c  # Cadeia de propagação prevista
  severity: [low | medium | high | critical]  # OBRIGATÓRIO: Severidade do impacto (padrão: medium se omitido)
  affected_domains: [lista de domínios afetados]
  propagation_estimate: [número estimado de UKIs impactadas]

lifecycle_management_ref: "uki:org.governance:policy:lifecycle-standard"  # OPCIONAL: referência UKI para política de ciclo de vida
# Referencia UKI organizacional que define condições de revisão, critérios de obsolescência,
# frequência de validação, ou condições para descontinuidade

intent_of_use:
  - [Lista de intenções específicas de uso desta UKI]
use_case_stage:
  - [Lista de etapas ou situações reais em que esta UKI é útil]
language: [pt_BR | en_US | ...]  # Idioma do conteúdo textual
content: |
  [Conteúdo principal da UKI — texto informativo, explicativo, técnico ou estratégico]
examples:
  - input: [Exemplo de entrada real ou simulada]
    output: [Resultado esperado ou consequência]
governance_ref: "uki:org.governance:policy:technical-standards"  # OPCIONAL: referência UKI para política de governança
# Referencia UKI organizacional que define criticidade, modo de propagação e frequência de validação
  impact_analysis:
    structural_changes: [breaking | compatible | additive]  # Impacto estrutural
    dependent_ukis: [number]  # Número estimado de UKIs dependentes
    propagation_scope: [immediate | scheduled | informative]  # Escopo de propagação
  propagation_rules:
    on_major_change: [notify_all | validate_dependencies | manual_review]
    on_minor_change: [suggest_updates | validate_compatibility | auto_notify]
    on_patch_change: [auto_propagate | inform_dependents | track_only]
provenance:  # OPCIONAL: histórico ou fonte da UKI
  author: [Nome ou identificador do criador da UKI]
  formulation_date: [YYYY-MM-DD]  # Data de formulação original
  original_instance: [Referência à fonte ou documento original]
  organization: [Organização ou equipe que criou a UKI]
  source_type: [meeting | document | interview | observation | analysis | experiment]
maturity_level: [draft | validated | endorsed | deprecated | experimental]  # OPCIONAL: nível de confiabilidade epistemológica
last_validation: [YYYY-MM-DD]  # Data da última revisão e validação de conteúdo
```

---

# 📘 DESCRIÇÃO DOS CAMPOS

## 🎯 Campos de Metadados Estruturais

### 🔹 `schema`
**Obrigatório** | **String** | **"2.0"**

Especifica a versão do **schema estrutural** (formato e layout YAML da UKI). Identifica mudanças no modelo de dados (novos campos, alterações obrigatórias, reorganização da estrutura).

- **Propósito**: Controle de versão da estrutura do arquivo
- **Usado para**: Validação de formato, migração automática, compatibilidade de parsers
- **Formato**: String com versão em formato semântico
- **Posição**: Primeiro campo do arquivo YAML

### 🔹 `ontology_reference`
**Obrigatório** | **String** | **"Ontology_MEF_Support v1.0"**

Referência à versão do vocabulário/ontologia que regula os valores controlados como `type`, `domain`, `status`, `relationship_types`, etc.

- **Propósito**: Garantir consistência semântica e validação automática
- **Justificativa do formato completo**: Evita ambiguidade entre diferentes ontologias, garante portabilidade e legibilidade
- **Formato**: `nome_da_ontologia + espaço + vX.Y`
- **Posição**: Segundo campo, imediatamente após `schema`

### 🔹 `version`
**Obrigatório** | **String** | **"MAJOR.MINOR.PATCH"**

Define a versão semântica da **UKI em si**, seguindo convenção de versionamento semântico para controle de mudanças conceituais.

- **Propósito**: Controle de evolução do conteúdo semântico da UKI
- **Diferente de**: `schema` (que versiona a estrutura do arquivo)
- **Formato**: String obrigatoriamente entre aspas (evita erro de parsing YAML)
- **Posição**: Terceiro campo, após `ontology_reference`

---

## 🎯 Campos de Identificação e Classificação

### 🔹 `id`
**Obrigatório** | **String** | **Único**

Identificador único seguindo o padrão `uki:[domain]:[type]:[identifier]`:
- **uki**: Prefixo fixo indicando uma Unidade de Conhecimento
- **domain**: Domínio organizacional (exemplos: product, business, technical - definidos no MOC organizacional)
- **identifier**: Slug descritivo ou código único

**Exemplos:**
- `uki:technical:pattern:jwt-authentication`
- `uki:example-org.business:rule:pricing-strategy`
- `uki:product:guideline:user-onboarding`

### 🔹 `title`
**Obrigatório** | **String**

Título claro, objetivo e descritivo que resume a unidade de conhecimento em uma frase.

**Diretrizes:**
- Máximo 80 caracteres
- Evitar jargão técnico quando possível
- Ser específico e acionável
- Usar formato imperativo ou descritivo

**Exemplos:**
- "Padrão de Implementação de Token JWT"
- "Regra de Cálculo de Precificação"
- "Fluxo de Onboarding de Usuário"

### 🔹 `scope_ref`
**Obrigatório** | **String**

Referência ao identificador de um nó de escopo definido no MOC (Matrix Ontology Catalog) da organização.

- **Propósito**: Define o alcance e visibilidade da UKI
- **Resolução**: Sistema consulta o MOC para aplicar regras de governança
- **Exemplos**: "personal", "team", "organization", "public"

### 🔹 `scope_mode`
**Obrigatório** | **Enum**

Modo de propagação e aplicabilidade do escopo. **Valores aceitos:**
- `restricted`: UKI limitada ao escopo especificado
- `propagated`: UKI pode ser propagada para escopos superiores conforme governança

### 🔹 `domain_ref`
**Obrigatório** | **String**

Referência ao identificador de um nó de domínio definido no MOC da organização. O sistema resolve automaticamente as regras de propriedade, revisão e autoridade baseadas na configuração do MOC.

**Conceitos universais (exemplos)**:
- Conhecimento técnico e implementação
- Regras e processos de negócio  
- Estratégia e planejamento organizacional
- Cultura e práticas colaborativas
- Segurança e compliance

**Implementação local**: Cada organização define no MOC seus domínios específicos e hierarquia.

### 🔹 `type_ref`
**Obrigatório** | **String**

Referência ao identificador de um nó de tipo definido no MOC da organização.

**Conceitos universais (exemplos)**:
- Padrões e templates reutilizáveis
- Regras de negócio e políticas
- Diretrizes e boas práticas
- Decisões e justificativas
- Exemplos e casos de uso

**Implementação local**: Cada organização define no MOC seus tipos específicos e critérios de classificação.

### 🔹 `context_ref`
**Opcional** | **String**

Referência ao identificador de um nó de contexto definido no MOC da organização, quando aplicável.

**Conceitos universais (exemplos)**:
- Descoberta e pesquisa
- Implementação e desenvolvimento
- Refinamento e otimização
- Qualidade e validação
- Documentação e suporte

### 🔹 `maturity_ref`
**Obrigatório** | **String**

Referência ao identificador de um nó de maturidade definido no MOC da organização.

**Conceitos universais**:
- **Pré-validação**: Rascunho, experimental
- **Validação**: Em revisão, sendo validado
- **Endosso**: Aprovado, confiável
- **Depreciação**: Obsoleto, descontinuado

**Implementação local**: Cada organização define no MOC seus níveis intermediários e critérios de progressão.


### 🔹 `version`
**Obrigatório** | **String**

Versionamento semântico seguindo formato `MAJOR.MINOR.PATCH` para controle de evolução da UKI.

**Regras:**
- `MAJOR`: Mudanças que quebram compatibilidade ou alteram significado fundamental
- `MINOR`: Adições compatíveis (novos exemplos, refinamentos, clarificações)
- `PATCH`: Correções menores (typos, ajustes de formatação, pequenas clarificações)

**Exemplos:**
- `"1.0.0"` - Versão inicial
- `"1.2.0"` - Adicionados novos exemplos
- `"2.0.0"` - Mudança fundamental na abordagem

### 🔹 `created_date`
**Obrigatório** | **Data (YYYY-MM-DD)**

Data de criação da primeira versão (1.0.0) da UKI.

**Propósito:**
- Rastrear ciclo de vida da UKI
- Referência histórica
- Avaliação de relevância baseada na idade

### 🔹 `last_modified`
**Obrigatório** | **Data (YYYY-MM-DD)**

Data da última modificação correspondente à versão atual.

**Propósito:**
- Verificação de consistência de versão
- Rastreamento de mudanças
- Indicação de atualização do conteúdo

### 🔹 `change_summary`
**Obrigatório para versões versionadas** | **String**

Resumo das alterações realizadas na UKI.

**Diretrizes:**
- Ser específico e acionável
- Descrever o que foi alterado, não o porquê
- Manter conciso mas informativo
- Usar tempo passado

**Exemplos:**
- `"Adicionado exemplo de timeout e melhorada documentação de códigos de erro"`
- `"Corrigido erro de digitação no cálculo da regra de negócio"`
- `"Reestruturada organização do conteúdo para maior clareza"`

### 🔹 `change_impact`
**Obrigatório para versões versionadas** | **Enum**

Classificação do impacto da mudança para a versão atual.

**Valores aceitos:**
- `major`: Mudança significativa que afeta compreensão ou aplicação
- `minor`: Adição ou melhoria compatível que mantém compatibilidade
- `patch`: Correção menor que não altera o significado

### 🔹 `previous_version`
**Opcional** | **String**

Referência à versão imediatamente anterior para rastreabilidade de evolução.

**Formato:** `MAJOR.MINOR.PATCH`
**Uso:** Obrigatório para UKIs versionadas
**Propósito:** Permitir navegação de versões e capacidades de rollback

### 🔹 `intent_of_use`
**Opcional** | **Lista de Strings**

Lista de intenções ou propósitos específicos para usar esta UKI.

**Valores comuns:**
- `validate_implementation`
- `generate_code`
- `understand_context`
- `make_decision`
- `solve_problem`
- `create_documentation`
- `train_team`
- `standardize_process`

### 🔹 `use_case_stage`
**Opcional** | **Lista de Strings**

Lista de estágios de desenvolvimento ou projeto onde esta UKI é mais útil.

**Valores comuns:**
- `planning`
- `design`
- `implementation`
- `testing`
- `deployment`
- `maintenance`
- `peer_review`
- `documentation`
- `training`

### 🔹 `language`
**Opcional** | **String** | **Padrão: en_US**

Idioma do conteúdo textual.

**Valores aceitos:**
- `pt_BR` (Português - Brasil)
- `en_US` (Inglês - Estados Unidos)
- `es_ES` (Espanhol - Espanha)
- `fr_FR` (Francês - França)
- *Outros códigos ISO conforme necessário*

### 🔹 `content`
**Obrigatório** | **String (multilinha)**

Conteúdo principal da UKI em **texto claro e estruturado**:

**Sugestões de estrutura:**
1. **Descrição breve** (1-2 frases)
2. **Detalhes e contexto** (parágrafos)
3. **Implementação** (se aplicável)
4. **Considerações importantes** (se aplicável)

**Diretrizes:**
- Usar linguagem clara e objetiva
- Incluir detalhes práticos
- Evitar jargão técnico excessivo
- Ser abrangente mas conciso
- Usar markdown para formatação se necessário

### 🔹 `examples`
**Opcional** | **Lista de Objetos**

Lista de exemplos práticos mostrando entrada e saída esperada.

**Estrutura:**
```yaml
examples:
  - input: "Descrição da entrada ou situação"
    output: "Resultado ou ação esperada"
  - input: "Outro exemplo de entrada"
    output: "Outra saída esperada"
```

**Diretrizes:**
- Fornecer exemplos realistas
- Cobrir diferentes cenários se possível
- Ser específico e acionável
- Incluir casos extremos quando relevante

### 🔹 `status`
**Obrigatório** | **Enum**

Controle de ciclo de vida da UKI para rastreabilidade e governança.

**Valores aceitos:**
- `active`: UKI ativa e em uso normal
- `deprecated`: UKI descontinuada mas ainda referenciada
- `archived`: UKI arquivada para consulta histórica

**Propósito:**
- Controlar ciclo de vida das UKIs
- Facilitar governança automatizada
- Evitar uso de conhecimento obsoleto
- Manter rastreabilidade histórica

### 🔹 `domain_of_influence`
**Recomendado** | **Enum**

Área de impacto estratégico da UKI para análise de governança avançada.

**Valores aceitos:**
- `strategy`: Impacto em decisões estratégicas
- `finance`: Impacto em aspectos financeiros
- `ethics`: Impacto em questões éticas ou compliance
- `operations`: Impacto em operações e processos

**Propósito:**
- Classificar impacto organizacional
- Priorizar revisões baseadas em área de influência
- Facilitar análise de riscos
- Orientar processos de aprovação

### 🔹 `relationships`
**Obrigatório** | **Lista de Objetos**

Ontologia formal de relacionamentos tipados com outras UKIs, substituindo relacionamentos livres por estrutura padronizada.

**Tipos de Relação Ontológica Formalizada:**

| Tipo | Descrição | Uso |
|------|-----------|-----|
| `depends_on` | Depende semanticamente de outra UKI | Dependências estruturais |
| `overrides` | Substitui ou anula o conteúdo de outra UKI | Substituições diretas |
| `conflicts_with` | Contradiz propositalmente outra UKI | Incompatibilidades intencionais |
| `complements` | Expande ou detalha outra UKI | Extensões colaborativas |
| `amends` | Corrige ou atualiza parcialmente | Correções e ajustes |
| `precedes` | Estabelece ordem ou prioridade | Sequências e hierarquias |
| `equivalent_to` | Representa equivalência semântica | Equivalências e sinônimos |

**Formato Ontológico Padronizado:**
```yaml
relationships:
  - type: overrides
    target: uki:security:rule:legacy-auth
    description: Substitui método de autenticação legado
  - type: depends_on
    target: uki:security:procedure:crypto-validation
    description: Requer procedimento de validação criptográfica
  - type: complements
    target: uki:example-org.governance:policy:session-management
    description: Complementa política de gerenciamento de sessão
  - type: precedes
    target: uki:operations:procedure:user-verification
    description: Deve ser executado antes da verificação do usuário
```

**Diretrizes de Uso:**
- Sempre usar formato `uki:[domain]:[type]:[identifier]` para referências
- Evitar duplicação de relacionamentos em outros campos
- Manter consistência ontológica entre tipos
- Documentar claramente a natureza específica da relação

### 🔹 `impact_analysis`
**Opcional** | **Objeto**

Análise de cadeia de impacto para prever propagação de mudanças.

**Estrutura:**
```yaml
impact_analysis:
  chain_preview:
    - uki:technical:pattern:auth → uki:product:template:login → uki:technical:pattern:session
    - uki:technical:pattern:auth → uki:technical:guideline:api-security
  severity: high
  affected_domains: [technical, business, product]
  propagation_estimate: 12
```

**Campos:**
- `chain_preview`: Cadeias de propagação previstas
- `severity`: Severidade do impacto (low, medium, high, critical) - **OBRIGATÓRIO quando impact_analysis está presente** (padrão: medium se omitido)
- `affected_domains`: Domínios potencialmente afetados
- `propagation_estimate`: Número estimado de UKIs impactadas

**Propósito:**
- Antecipar impactos de mudanças
- Facilitar planejamento de atualizações
- Priorizar revisões baseadas em severidade
- Orientar estratégias de comunicação

### 🔹 `lifecycle_management_ref`
**Opcional** | **String (UKI Reference)**

Referência para UKI organizacional que define política de revisão, avaliação ou descontinuidade.

**Exemplos de Uso:**
```yaml
lifecycle_management_ref: "uki:acme-corp.governance:policy:security-quarterly"
# Aponta para UKI organizacional que define:
# - Esta UKI deve ser revisada trimestralmente devido ao impacto em segurança
# - Considerar deprecação se novas tecnologias de autenticação forem adotadas
# - Critérios para arquivamento: substituição completa por OAuth3 ou similar
```

**Conteúdo Recomendado:**
- Frequência de revisão específica
- Critérios para deprecação
- Condições para arquivamento
- Marcos tecnológicos ou organizacionais relevantes

**Propósito:**
- Definir ciclo de vida específico da UKI
- Orientar decisões de manutenção
- Facilitar planejamento de descontinuidade
- Documentar dependências de contexto externo

### 🔹 `promotion`
**Opcional** | **Objeto**

Campos específicos para registro e rastreabilidade de promoção de UKIs, permitindo a transição formal de conhecimento de escopo limitado para amplo.

**Campos:**
- `is_promoted_from`: Referência à UKI original da qual esta foi promovida
- `promotion_rationale`: Justificativa detalhada da promoção com evidências e motivos

**Formato:**
```yaml
promotion:
  is_promoted_from: uki:technical:pattern:jwt-local-implementation
  promotion_rationale: |
    Promovida devido à adoção recorrente em 5 projetos diferentes,
    demonstrando valor consolidado e aplicabilidade generalizada.
    Evidências: 15 implementações bem-sucedidas, feedback positivo
    de 3 equipes diferentes, e alinhamento com estratégia de segurança.
```

**Propósito:**
- Estabelecer rastreabilidade específica entre UKI original e promovida
- Documentar justificativas para elevação de escopo
- Preservar continuidade semântica no processo de promoção
- Facilitar auditoria de decisões de maturação do conhecimento

**Diretrizes:**
- Usar apenas quando UKI for resultado de promoção
- Sempre preencher `is_promoted_from` com referência à UKI original
- Documentar evidências observáveis na `promotion_rationale`
- O campo `is_promoted_from` tem escopo específico para promoções

### 🔹 `provenance`
**Opcional** | **Objeto**

Histórico ou fonte da UKI para rastreamento de origem e autoria.

**Campos:**
- `author`: Nome ou identificador do criador
- `formulation_date`: Data de formulação original 
- `original_instance`: Referência à fonte original
- `organization`: Organização ou equipe criadora
- `source_type`: Tipo de fonte (meeting, document, interview, observation, analysis, experiment)

**Propósito:**
- Rastreabilidade de conhecimento
- Atribuição de autoria
- Contexto histórico
- Validação de fonte

### 🔹 `maturity_level`
**Opcional** | **Enum**

Nível de confiabilidade epistemológica da UKI. **Valores aceitos:**

| Nível | Descrição | Confiança | Recomendação de Uso |
|-------|-----------|-----------|---------------------|
| `draft` | Formulação inicial, sujeita a revisão | Baixa | Usar com cautela, verificar independentemente |
| `validated` | Revisado por especialistas do domínio | Média | Confiável para implementação com verificação padrão |
| `endorsed` | Oficialmente aprovado pela organização | Alta | Fonte autoritativa, usar como referência padrão |
| `deprecated` | Não recomendado, substituído | Baixa | Evitar uso, referir a UKI substituta |
| `experimental` | Em avaliação, implementação piloto | Variável | Usar apenas em ambientes controlados |

### 🔹 `last_validation`
**Opcional** | **Data (YYYY-MM-DD)**

Data da última revisão e validação do conteúdo.

**Propósito:**
- Controle de qualidade
- Atualização do conteúdo
- Planejamento de manutenção
- Indicação de confiabilidade

### 🔹 `governance_ref`
**Opcional** | **String (UKI Reference)**

Referência para UKI organizacional que define configurações de governança ativa para controle automático de propagação e impacto.

**Exemplo de Uso:**
```yaml
governance_ref: "uki:acme-corp.governance:policy:critical-technical-policy"
# Aponta para UKI organizacional que define:
# - criticality: critical
# - auto_propagation: manual
# - validation_frequency: 30
  impact_analysis:
    structural_changes: [breaking | compatible | additive]
    dependent_ukis: [number]
    propagation_scope: [immediate | scheduled | informative]
  propagation_rules:
    on_major_change: [notify_all | validate_dependencies | manual_review]
    on_minor_change: [suggest_updates | validate_compatibility | auto_notify]
    on_patch_change: [auto_propagate | inform_dependents | track_only]
```

#### **`criticality`** - Nível de Criticidade
- `critical`: UKI essencial para funcionamento básico do sistema
- `high`: UKI importante com impacto significativo em implementações
- `medium`: UKI padrão com relevância moderada
- `low`: UKI informativa ou de baixo impacto

#### **`auto_propagation`** - Modo de Propagação
- `automatic`: Propagação automática para todas as mudanças
- `semi_automatic`: Proposta automática com aprovação manual
- `manual`: Processo totalmente manual de propagação

#### **`validation_frequency`** - Frequência de Validação
Número de dias entre revisões obrigatórias do conteúdo.

#### **`impact_analysis`** - Análise de Impacto
- `structural_changes`: Tipo de impacto estrutural esperado
- `dependent_ukis`: Estimativa de UKIs que dependem desta
- `propagation_scope`: Escopo necessário de propagação

#### **`propagation_rules`** - Regras de Propagação
Define comportamento específico para cada tipo de mudança de versão.

**Propósito:**
- Automatizar governança de conhecimento
- Controlar propagação de mudanças
- Manter consistência entre UKIs relacionadas
- Priorizar revisões baseadas em criticidade

---

# 🧩 TIPOS DE CONTEÚDO E FORMAS DE EMBEDAMENTO

Esta seção descreve os tipos de conteúdo suportados pelo protocolo MEF e como devem ser convertidos para estruturas textuais aptas a serem embebidas e utilizadas por agentes.

## 🎙️ Áudio (podcasts, entrevistas, reuniões gravadas)

* **Conversão necessária:** Transcrição automática via modelo ASR (ex: Whisper, AssemblyAI).
* **Pós-processamento:**

  * Dividir por tópicos (com timestamps opcionais).
  * Remover ruídos e hesitações.
  * Identificar e estruturar regras, decisões, padrões mencionados.
* **Formato final:** YAML com `content:` textual, exemplo:

```yaml
content: |
  A reunião descreve a nova regra de expiração de token:
  - O token expira após 15 min de inatividade.
  - Reemissão é automática se o usuário ainda estiver logado.
```

## 📹 Vídeo (gravações, aulas, demonstrações)

* **Conversão necessária:**

  * Transcrição de áudio como no áudio.
  * OCR ou descrição automatizada da tela (visão computacional).
  * Extração de elementos textuais falados e visuais.
* **Formato recomendado:** Criação de múltiplas UKIs por tópico, diagrama ou decisão extraída. Exemplos:

````yaml
content: |
  O vídeo apresenta o seguinte fluxo:
````
```mermaid
  sequenceDiagram
    User->>FE: Login
    FE->>Auth0: Solicita token
    Auth0-->>FE: JWT
    FE->>BE: Envia JWT
    BE-->>FE: Confirmação
````

## 🖼️ Imagens (telas, capturas, diagramas não estruturados)
- **Conversão necessária:** OCR + descrição semântica.
- **Uso ideal:** Apoio complementar com descrição estruturada no campo `content:`.
- **Recomendação:** Sempre que possível, recriar em `mermaid` ou Markdown.

## 🔄 Diagramas, fluxos e UML
- **Formato oficial recomendado:** `mermaid`
- **Justificativa:**
  - Compatível com renderização e leitura por LLMs.
  - Suporta fluxogramas, diagramas de sequência, máquinas de estado, diagramas de classe.
- **Exemplo:**
```yaml
content: |
```
```mermaid
  stateDiagram-v2
    [*] --> Autenticando
    Autenticando --> Autenticado : sucesso
    Autenticando --> Erro : falha
````

## 💬 Texto puro (documentos, emails, specs)
- **Tratamento necessário:**
  - Separação em unidades atômicas de conhecimento.
  - Limpeza de ruídos, redundâncias e linguagem informal.
- **Conversão para uki-**
  - Estruturar como `content:` com exemplos e campos semânticos preenchidos.

---

# 📁 ORGANIZAÇÃO DO REPOSITÓRIO

### Estrutura sugerida:

```
knowledge-source/
├── product/
├── business/
├── technical/
├── strategy/
├── culture/
```

Cada pasta conterá arquivos `.yaml` conforme o domínio correspondente.

Essa separação garante organização semântica, versionamento independente por área e melhor navegação para humanos e agentes.

---

# ✅ DIRETRIZES DE USO

## 📋 Diretrizes Gerais

- Toda UKI deve ser modular, clara e versionada adequadamente.
- Os campos `intent_of_use` e `use_case_stage` são obrigatórios e são chave para inteligência contextual.
- `language` ajuda agentes a priorizar, traduzir ou adaptar sugestões.
- Sempre que possível, utilizar sintaxe `mermaid` para diagramas textuais.
- Versionamento semântico garante evolução controlada e rastreabilidade do conhecimento.
- Iniciar sempre com versão 1.0.0 para novas UKIs.
- Incrementar MAJOR para mudanças que alterem significativamente o significado ou aplicação.
- Incrementar MINOR para adições compatíveis (novos exemplos, refinamentos, clarificações).
- Incrementar PATCH para correções menores (typos, ajustes de formatação, pequenas clarificações).
- Documentar mudanças no campo `change_summary` quando aplicável.
- Manter rastreabilidade através do campo `previous_version`.

## 🔥 Diretrizes para Campos Estruturais

### 🎯 **Campo `status` (Obrigatório)**
- **SEMPRE** definir status inicial como `active` para novas UKIs
- Usar `deprecated` quando UKI não deve mais ser usada mas ainda é referenciada
- Usar `archived` apenas para UKIs descontinuadas mantidas para consulta histórica
- **NUNCA** deletar UKIs - apenas mudar status para manter rastreabilidade

### 🔗 **Campo `relationships` (Obrigatório)**
- Usar formato `uki:[domain]:[type]:[identifier]` para referências
- **Escolher tipos precisos**: ontológicos para relações estruturais, semânticos para conceituais
- **USAR APENAS** tipos de relacionamento da ontologia: depends_on, overrides, conflicts_with, complements, amends, precedes, equivalent_to
- **VALIDAR** que target existe antes de criar relacionamento
- **DOCUMENTAR** claramente a natureza específica de cada relação

### 🌍 **Campo `domain_of_influence` (Recomendado)**
- Organizações podem configurar para UKIs com impacto organizacional significativo
- **Valores exclusivamente definidos no MOC organizacional**

**🚨 Importante**: Os exemplos abaixo são **puramente ilustrativos** e **não constituem taxonomia oficial**:

> Algumas organizações podem configurar domínios como "estratégia" para decisões de alto nível, "finanças" para regras de impacto financeiro, "ética" para questões de compliance, ou "operações" para eficiência processual. Outras podem usar termos completamente diferentes como "inovação", "qualidade", "sustentabilidade" ou qualquer hierarquia que faça sentido em seu contexto.

**🏛️ MOC é a fonte única**: Cada organização define seus próprios domínios de influência exclusivamente no Matrix Ontology Catalog.

### 📊 **Campo `impact_analysis` (Opcional)**
- **MAPEAR** cadeias de propagação previstas antes de mudanças MAJOR
- Estimar número realista de UKIs impactadas
- Usar severity `critical` apenas para UKIs que quebram funcionalidade básica
- **ATUALIZAR** quando relacionamentos mudarem significativamente

### 📅 **Campo `lifecycle_management_ref` (Opcional)**
- **DEFINIR** referência UKI para UKIs críticas ou que dependem de tecnologias externas
- Referenciar UKI organizacional com critérios objetivos para revisão e descontinuidade
- **MENCIONAR** marcos tecnológicos ou organizacionais relevantes
- Ser específico sobre frequência de revisão (trimestral, semestral, anual)

## ⚠️ Diretrizes de Coerência Semântica

- **EVITAR** duplicação de informações entre campos `relationships` e outros campos
- **MANTER** consistência ontológica: se A `overrides` B, então B deve estar `deprecated`
- **VALIDAR** que UKIs com status `deprecated` não sejam target de novos relacionamentos `depends_on`
- **VERIFICAR** que `domain_of_influence` seja coerente com `domain` e `type`
- **GARANTIR** que `impact_analysis.severity` seja proporcional ao número de relacionamentos

## 🔄 Governança de Mudanças

- **ANALISAR** impacto em UKIs relacionadas antes de mudanças MAJOR
- **PROPAGAR** mudanças seguindo a ontologia de relacionamentos
- **NOTIFICAR** stakeholders baseado em `domain_of_influence`
- **REAVALIAR** `lifecycle_management_ref` quando contexto organizacional mudar
- **MANTER** histórico de versões para auditoria e rollback

---

# 🤖 CONSUMO POR AGENTES

Agentes Matrix podem:
- Inferir relações entre padrões, código e regras de negócio
- Sugerir UKIs relevantes durante workflows reais
- Detectar incoerências ou violações de padrões
- Validar implementações conforme decisões e diretrizes da equipe
- Gerar novos conteúdos baseados em UKIs existentes (ex: histórias de usuário, testes, documentação)

---

# 📊 STATUS

**Protocolo Matrix MEF - Versão 1.0**
**Aprovado pelo Conselho Oráculo**
**Ativo para uso imediato em toda a Matrix**

---

# 🌐 VISÃO DE EXPANSÃO FUTURA

Embora o foco atual do MEF seja a estruturação de conhecimento no contexto de engenharia de software, o modelo foi concebido para ser escalável e aplicável em outros contextos organizacionais. A evolução do protocolo prevê sua utilização em múltiplas camadas de conhecimento, permitindo uma base unificada e interoperável entre áreas.

## Camadas de Aplicação do MEF

| Camada              | Público-alvo                                 | Uso principal                                           |
|---------------------|----------------------------------------------|--------------------------------------------------------|
| Core Engineering    | Times de engenharia (PMs, Tech Leads, Devs, Analysts) | Regras, código, especificações técnicas, arquitetura, regras de negócio, fluxos internos da squad |
| Organizational Ops  | Produto, Jurídico, Compliance                | Políticas, fluxos interdepartamentais, decisões operacionais |
| Support Knowledge   | Atendimento, Onboarding, Suporte            | Procedimentos, scripts operacionais, documentação útil |

### Diretrizes de aplicação por camada:
- Cada camada pode utilizar a **mesma estrutura de UKI**, mantendo consistência semântica.
- É possível **expandir domínios e tipos** conforme as necessidades de cada escopo.
- Os conteúdos podem ser armazenados em **repositórios independentes**, mas seguindo o **mesmo framework base**.

Esse modelo garante que a Matrix se expanda como uma base de conhecimento orgânica e contextual, conectando diferentes times sem sacrificar a padronização e a governança.

---

# 📋 EXEMPLOS PRÁTICOS DE UKIs

## Exemplo 1: Padrão Técnico

```yaml
schema: "1.0"
ontology_reference: "Ontology_MEF_Support v1.0"
version: "1.0.0"

id: uki:technical:pattern:api-error-handling
title: Padrão de Tratamento de Erros em API
domain: technical
type: pattern
context: implementation
created_date: "2024-01-15"
last_modified: "2024-01-15"

status: active
domain_of_influence: operations

relationships:
  - type: depends_on
    target: uki:technical:template:api-response-format
    description: Implementa formato padrão de resposta da API com estrutura de erro
  - type: complements
    target: uki:technical:guideline:logging-standards
    description: Complementa padrões de logging para auditoria e debugging
  - type: depends_on
    target: uki:[domain]:[type]:[identifier]
    description: Depende de definições padronizadas de códigos HTTP

impact_analysis:
  chain_preview:
    - uki:[domain]:[type]:[identifier] → uki:[domain]:[type]:[identifier]
    - uki:[domain]:[type]:[identifier] → uki:[domain]:[type]:[identifier]
  severity: medium
  affected_domains: [technical, product]
  propagation_estimate: 8

lifecycle_management_ref: "uki:example-org.governance:policy:api-standards-annual"
# Referencia UKI organizacional que define:
# - Revisar anualmente ou quando novos padrões de API forem adotados
# - Considerar deprecação se GraphQL ou outras tecnologias substituirem REST
  Arquivar apenas após migração completa de todas as APIs.

intent_of_use:
  - standardize_error_responses
  - improve_api_consistency
  - facilitate_debugging
use_case_stage:
  - implementation
  - peer_review
  - testing
language: pt_BR
content: |
  Padrão padronizado para tratamento e retorno de erros em APIs REST.
  
  Estrutura de resposta de erro:
  '''json
  {
    "error": {
      "code": "VALIDATION_ERROR",
      "message": "Dados inválidos fornecidos",
      "details": [
        {
          "field": "email",
          "message": "Email deve ter formato válido"
        }
      ],
      "timestamp": "2024-01-15T10:30:00Z",
      "request_id": "uuid-123-456"
    }
  }
  '''
  
  Códigos de status HTTP:
  - 400: Erro de validação ou request malformado
  - 401: Não autenticado
  - 403: Não autorizado
  - 404: Recurso não encontrado
  - 500: Erro interno do servidor
examples:
  - input: "Erro de validação de email inválido"
    output: "Status 400 com código VALIDATION_ERROR e detalhes do campo email"
  - input: "Tentativa de acesso sem token JWT"
    output: "Status 401 com código AUTHENTICATION_REQUIRED"
last_validation: "2024-01-15"
```

## Exemplo 2: Regra de Negócio
```yaml
schema: "1.0"
ontology_reference: "Ontology_MEF_Support v1.0"
version: "1.2.0"

id: uki:business:rule:discount-calculation
title: Regra de Cálculo de Desconto de Cliente
domain: business
type: business_rule
context: implementation
created_date: "2024-01-10"
last_modified: "2024-01-15"
change_summary: "Adicionado desconto para clientes premium e limite máximo"
change_impact: "minor"
previous_version: "1.1.0"

status: active
domain_of_influence: finance

relationships:
  - type: depends_on
    target: uki:[domain]:[type]:[identifier]
    description: Implementa regras do programa de fidelidade para cálculo automático
  - type: complements
    target: uki:[domain]:[type]:[identifier]
    description: Complementa processo de checkout com lógica de preço final
  - type: depends_on
    target: uki:[domain]:[type]:[identifier]
    description: Depende de classificação de perfil de cliente para funcionar
  - type: overrides
    target: uki:[domain]:[type]:[identifier]
    description: Substitui regras de desconto manuais anteriores

impact_analysis:
  chain_preview:
    - uki:[domain]:[type]:[identifier] → uki:[domain]:[type]:[identifier] → uki:[domain]:[type]:[identifier]
    - uki:[domain]:[type]:[identifier] → uki:[domain]:[type]:[identifier]
  severity: high
  affected_domains: [business, finance, product]
  propagation_estimate: 15

lifecycle_management_ref: "uki:example-org.governance:policy:business-quarterly"
# Referencia UKI organizacional que define:
# - Revisar trimestralmente devido ao impacto financeiro direto
# - Reavaliar se novos modelos de fidelidade forem implementados
  Arquivar apenas após substituição por sistema de pricing dinâmico.

intent_of_use:
  - calculate_customer_discounts
  - ensure_pricing_consistency
  - automate_business_logic
use_case_stage:
  - implementation
  - testing
  - training
language: pt_BR
content: |
  Regra para calcular desconto automático baseado no perfil e histórico do cliente.
  
  Cálculo de desconto:
  1. Cliente Novo (< 3 meses): 5%
  2. Cliente Regular (3-12 meses): 10%
  3. Cliente Fiel (> 12 meses): 15%
  4. Cliente Premium: +5% adicional
  5. Desconto máximo: 25%
  
  Fórmula:

  desconto_base = perfil_cliente.desconto_percentual
  desconto_premium = cliente.is_premium ? 5 : 0
  desconto_total = min(desconto_base + desconto_premium, 25)
  valor_final = valor_original * (1 - desconto_total/100)

examples:
  - input: "Cliente fiel premium comprando R$ 1000"
    output: "Desconto 20% (15% + 5%), valor final R$ 800"
  - input: "Cliente novo comprando R$ 500"
    output: "Desconto 5%, valor final R$ 475"
last_validation: "2024-01-15"
```

## Exemplo 3: Diretriz de Produto
```yaml
schema: "1.0"
ontology_reference: "Ontology_MEF_Support v1.0"
version: "1.0.0"

id: uki:product:guideline:modal-design
title: Diretrizes de Design para Modais
domain: product
type: guideline
context: design
created_date: "2024-01-08"
last_modified: "2024-01-08"

status: active
domain_of_influence: operations

relationships:
  - type: depends_on
    target: uki:[domain]:[type]:[identifier]
    description: Implementa componentes padronizados do sistema de design
  - type: depends_on
    target: uki:[domain]:[type]:[identifier]
    description: Depende de padrões de acessibilidade para compliance
  - type: complements
    target: uki:[domain]:[type]:[identifier]
    description: Complementa biblioteca de componentes com especificações de modal

impact_analysis:
  chain_preview:
    - uki:[domain]:[type]:[identifier] → uki:[domain]:[type]:[identifier] → uki:[domain]:[type]:[identifier]
    - uki:[domain]:[type]:[identifier] → uki:[domain]:[type]:[identifier]
  severity: medium
  affected_domains: [product, technical]
  propagation_estimate: 6

lifecycle_management_ref: "uki:example-org.governance:policy:ui-semiannual"
# Referencia UKI organizacional que define:
# - Revisar semestralmente com time de design e acessibilidade
# - Reavaliar quando novos frameworks de UI forem adotados
  Considerar atualização major se padrões de acessibilidade mudarem.

intent_of_use:
  - standardize_ui_components
  - guide_design_decisions
  - ensure_accessibility
use_case_stage:
  - design
  - implementation
  - peer_review
language: pt_BR
content: |
  Diretrizes para criar modais consistentes e acessíveis na aplicação.
  
  Princípios fundamentais:
  1. Use modais moderadamente - apenas para ações críticas ou informações importantes
  2. Sempre forneça uma forma clara de fechar (botão X + tecla ESC)
  3. Inclua ação primária e secundária quando apropriado
  4. Use tamanhos apropriados (pequeno: 400px, médio: 600px, grande: 800px)
  5. Centre vertical e horizontalmente
  6. Inclua gestão adequada de foco para acessibilidade
  
  Estrutura do modal:
  - Cabeçalho: Título + botão fechar
  - Corpo: Conteúdo principal com hierarquia clara
  - Rodapé: Botões de ação (primário à direita, secundário à esquerda)
examples:
  - input: "Confirmar ação de exclusão"
    output: "Modal médio com botões 'Excluir' (perigo) e 'Cancelar'"
  - input: "Exibir informações do perfil do usuário"
    output: "Modal grande com botões 'Editar Perfil' e 'Fechar'"
last_validation: "2024-01-08"
```

---

# 🔄 RELACIONAMENTOS SEMÂNTICOS

## Relacionamentos Semânticos Tipados

O MEF utiliza relacionamentos semânticos tipados para construir grafos de conhecimento ricos e habilitar governança automatizada entre UKIs.

### 🏗️ **Dependências de Implementação** (`depends_on`)
UKIs que implementam padrões ou dependem de outros conhecimentos para funcionalidade.

**Exemplos:**
```yaml
# uki:technical:function:jwt-implementation
relationships:
  - target: uki:technical:function:jwt-validation
    type: depends_on
    description: Requer lógica de validação JWT para funcionar adequadamente
  - target: uki:technical:pattern:authentication
    type: depends_on
    description: Implementa o padrão de autenticação padronizado
```

### 🌿 **Evolução do Conhecimento** (`complements` / `amends` / `overrides`)
UKIs que representam evolução, especialização ou substituição de conhecimento.

**Exemplos:**
```yaml
# uki:technical:function:oauth2-implementation
relationships:
  - target: uki:technical:pattern:oauth-basic
    type: complements
    description: Estende OAuth básico com PKCE e refresh tokens
  - target: uki:technical:pattern:legacy-auth
    type: overrides
    description: Substitui método de autenticação descontinuado
```

### 🛡️ **Relacionamentos de Conformidade** (`complies_with` / `conflicts_with`)
UKIs que seguem políticas ou identificam incompatibilidades.

**Exemplos:**
```yaml
# uki:technical:guideline:encryption-standard
relationships:
  - target: uki:example-org.business:policy:data-protection
    type: complies_with
    description: Segue requisitos de proteção de dados corporativos
  - target: uki:technical:pattern:legacy-encryption
    type: conflicts_with
    description: Incompatível com métodos de criptografia descontinuados
```

### 🌐 **Associações Contextuais** (`complements`)
Relacionamentos para conexões contextuais que expandem ou detalham outras UKIs.

**Exemplo:**
```yaml
# uki:example-org.governance:policy:user-onboarding
relationships:
  - target: uki:security:procedure:user-registration-api
    type: complements
    description: Expande contexto no domínio de gestão de usuários
  - target: uki:example-org.strategy:rule:user-retention-strategy
    type: depends_on
    description: Fundamenta-se na estratégia de retenção de usuários
```

## Diretrizes de Relacionamento

1. **Precisão Semântica**: Use tipos específicos de relação quando aplicável
2. **Consistência Bidirecional**: Garanta que relacionamentos reversos façam sentido semântico
3. **Descrições Claras**: Sempre forneça descrições significativas para cada relacionamento
4. **Governança Habilitada**: Relacionamentos tipados permitem análise de impacto e validação automatizada

# 🎛️ GOVERNANÇA ATIVA E PROPAGAÇÃO AUTOMÁTICA

O MEF implementa um sistema de **governança ativa** que utiliza relacionamentos semânticos tipados para propagar automaticamente mudanças e manter consistência em redes de conhecimento interconectadas.

## 🔄 Regras de Propagação por Tipo de Relacionamento

### 📋 **`depends_on`** - Propagação de Padrões
**Regra:** Mudanças em padrões/diretrizes devem ser propagadas para suas implementações.

**Comportamento:**
- **MAJOR**: Notificar implementações sobre incompatibilidade
- **MINOR**: Sugerir adoção de melhorias opcionais
- **PATCH**: Informar correções aplicáveis

**Algoritmo:**
```yaml
when: change in base-UKI (pattern/guideline)
propagation:
  to: UKIs where { type: depends_on, target: base-UKI }
  action: 
    - major: mark as "requires_review"
    - minor: mark as "improvement_available"
    - patch: mark as "correction_available"
```

### 🏗️ **`depends_on`** - Validação de Dependências
**Regra:** Mudanças em dependências devem validar compatibilidade dos dependentes.

**Comportamento:**
- **MAJOR**: Verificar quebra de compatibilidade
- **MINOR**: Validar funcionamento continuado
- **PATCH**: Verificar se correção afeta dependente

**Algoritmo:**
```yaml
when: change in dependency-UKI
propagation:
  to: UKIs where { type: depends_on, target: dependency-UKI }
  action:
    - major: execute "compatibility_analysis"
    - minor: execute "functional_validation"
    - patch: execute "impact_verification"
```

### 🌿 **`complements`** - Extensões
**Regra:** Mudanças em conceitos base devem ser avaliadas para extensões.

**Comportamento:**
- **MAJOR**: Avaliar se extensão ainda é válida
- **MINOR**: Considerar incorporação de melhorias
- **PATCH**: Verificar relevância da correção

**Algoritmo:**
```yaml
when: change in base-UKI
propagation:
  to: UKIs where { type: complements, target: base-UKI }
  action:
    - major: mark as "extension_requires_review"
    - minor: mark as "consider_incorporation"
    - patch: mark as "assess_relevance"
```

### 🔄 **`overrides`** - Deprecação Automática
**Regra:** Mudanças em substitutos devem atualizar status de substituídos.

**Comportamento:**
- **MAJOR**: Marcar substituído como descontinuado
- **MINOR**: Atualizar recomendação de migração
- **PATCH**: Informar sobre melhorias do substituto

**Algoritmo:**
```yaml
when: change in replacement-UKI
propagation:
  to: UKIs where { type: overrides, source: replacement-UKI }
  action:
    - major: mark as "discontinued"
    - minor: update "migration_plan"
    - patch: update "replacement_reasons"
```

### 🛡️ **`complies_with`** - Validação de Conformidade
**Regra:** Mudanças em políticas devem validar conformidade continuada.

**Comportamento:**
- **MAJOR**: Revisar toda conformidade
- **MINOR**: Verificar conformidade continuada
- **PATCH**: Confirmar que correção não afeta conformidade

### ⚔️ **`conflicts_with`** - Detecção de Conflitos
**Regra:** Mudanças podem resolver ou agravar conflitos existentes.

**Comportamento:**
- **MAJOR**: Reavaliar natureza do conflito
- **MINOR**: Verificar se conflito persiste
- **PATCH**: Confirmar que correção não cria novos conflitos

## 🧠 Algoritmos de Análise de Impacto

### 📊 Classificação de Impacto por Mudança

```yaml
impact_analysis:
  chain_preview:
    - uki:technical:pattern:change → uki:product:guideline:ui-patterns → uki:business:rule:validation
  severity: medium  # Campo obrigatório com fallback padrão
  affected_domains: [technical, product, business]
  propagation_estimate: 3
  change_scope:
    structural: "mandatory fields changed"
    semantic: "fundamental meaning changed"
    implementation: "examples or details changed"
    correction: "typos or minor clarifications"
  
  impact_types:
    critical: "breaks existing functionality"
    high: "requires implementation adaptation"
    medium: "recommends review and adaptation"
    low: "informational, no action needed"
  
  required_propagation:
    immediate: "critical implementations"
    scheduled: "planned improvements"
    informative: "knowledge updates"
```

### 🎯 Matriz de Priorização de Propagação

| Tipo Mudança | Relacionamento | Prioridade | Ação |
|--------------|----------------|------------|------|
| MAJOR | depends_on | CRÍTICA | Revisão obrigatória |
| MAJOR | depends_on | CRÍTICA | Validação compatibilidade |
| MAJOR | complements | ALTA | Revisão extensão |
| MINOR | depends_on | MÉDIA | Considerar adoção |
| MINOR | depends_on | MÉDIA | Validar funcionamento |
| PATCH | qualquer | BAIXA | Informar disponibilidade |

### 🔄 Algoritmo de Cascata de Versionamento

```yaml
cascade_versioning:
  trigger: "change in source-UKI"
  process:
    identify_related:
      query: "SELECT * FROM ukis WHERE relationships.target = source-UKI"
    classify_impact:
      for_each: relationship
      calculate: impact_by_type[relationship.type]
    generate_proposals:
      for_each: related-UKI
      propose: new_version_based_on_impact
    execute_propagation:
      order: priority (critical → high → medium → low)
      mode: automatic | semi-automatic | manual
```

## 🚨 Detecção de Conflitos e Inconsistências

### 🔍 Validações Automáticas

```yaml
validations:
  semantic_consistency:
    - "UKI que depends_on deve ser compatível com target"
    - "UKI que overrides deve ter domain similar ao target"
    - "UKI que complements deve manter compatibilidade base"
  
  reference_integrity:
    - "Todos relationships.target devem existir"
    - "Versões previous_version devem existir"
    - "Relacionamentos bidirecionais devem ser consistentes"
  
  content_quality:
    - "Mudanças MAJOR devem ter change_summary detalhado"
    - "UKIs críticos devem ter last_validation recente"
    - "Exemplos devem ser consistentes com content"
```

### ⚠️ Alertas de Governança

```yaml
alerts:
  pending_propagation:
    - "UKI-X foi atualizada, 5 implementações precisam de revisão"
    - "Nova versão MAJOR de padrão crítico disponível"
  
  detected_conflicts:
    - "UKI-A conflicts_with UKI-B, mas ambas marcadas como ativas"
    - "Dependência circular detectada: A→B→C→A"
  
  degraded_quality:
    - "UKI crítica não validada há 90+ dias"
    - "Relacionamento órfão: target não existe"
```

## 🎛️ Configuração de Governança

### 📋 Configurações por Tipo de UKI

```yaml
governance_config:
  critical_ukis:
    domains: [business, technical]
    types: [business_rule, pattern]
    validation_frequency: 30  # dias
    auto_propagation: semi-automatic
  
  standard_ukis:
    domains: [product, culture, strategy]
    types: [guideline, template, example]
    validation_frequency: 90  # dias
    auto_propagation: manual
```

### 🔄 Modos de Propagação

```yaml
propagation_modes:
  automatic:
    description: "Propagação automática para mudanças PATCH"
    scope: "Correções menores e atualizações informativas"
  
  semi_automatic:
    description: "Proposta automática, aprovação manual"
    scope: "Mudanças MINOR em UKIs críticas"
  
  manual:
    description: "Processo totalmente manual"
    scope: "Mudanças MAJOR e decisões estratégicas"
```

# 📚 ONTOLOGIA AUXILIAR

## Vocabulário Controlado para Campos MEF

Esta seção define o vocabulário controlado aceito para os campos `domain`, `type`, `severity`, `relationship.type`, `maturity_level` e `provenance.source_type` para garantir consistência semântica em implementações de UKIs.

### Domínios (`domain`)

| Domínio | Descrição | Exemplos |
|---------|-----------|----------|
| `strategy` | Decisões de alto nível, planejamento estratégico | Roadmaps, decisões estratégicas, direcionamento organizacional |
| `operations` | Processos operacionais, execução e procedimentos | Fluxos de trabalho, procedimentos operacionais, execução de tarefas |
| `ethics` | Considerações éticas, compliance e responsabilidade | Políticas de conduta, conformidade regulatória, responsabilidade social |
| `finance` | Aspectos financeiros, orçamentários e econômicos | Custos, receitas, ROI, decisões de investimento |
| `security` | Segurança, proteção e gerenciamento de riscos | Políticas de segurança, controles de acesso, gestão de vulnerabilidades |
| `governance` | Governança, controle e supervisão | Políticas de governança, estruturas de controle, supervisão organizacional |
| `communication` | Comunicação, colaboração e relacionamentos | Protocolos de comunicação, fluxos informativos, relacionamentos |
| `automation` | Automação, eficiência e otimização de processos | Processos automatizados, otimizações, eficiência operacional |
| `intelligence` | Inteligência, análise e tomada de decisão | Análises estratégicas, insights, suporte à decisão |

### Tipos (`type`)

| Tipo | Descrição | Uso |
|------|-----------|-----|
| `concept` | Definição ou modelo teórico | Conceituação, estruturas de pensamento |
| `rule` | Regra operacional ou normativa | Validação, lógica de decisão, normas |
| `metric` | Indicador quantitativo | Medição, avaliação, monitoramento |
| `policy` | Diretriz institucional ou adaptativa | Orientação organizacional, políticas |
| `procedure` | Sequência operacional | Processos, fluxos de trabalho, execução |
| `glossary` | Definição de termos ou padrões | Padronização terminológica, referências |
| `constraint` | Limitação formal aplicada | Restrições, limitações, controles |

### Níveis de Severidade (`severity`)

| Nível | Descrição | Impacto |
|-------|-----------|---------|
| `low` | Impacto menor, informacional ou sugestões de melhoria | Impacto mínimo nos negócios ou técnico |
| `medium` | Impacto moderado, afeta funcionalidades ou processos específicos | Impacto localizado na funcionalidade ou experiência do usuário |
| `high` | Impacto significativo, afeta funcionalidades centrais ou operações de negócio | Impacto substancial na funcionalidade do sistema ou processos de negócio |
| `critical` | Impacto crítico, falha do sistema ou grande disrupção de negócio | Impacto severo causando falha do sistema ou grande disrupção de negócio |

### Tipos de Relacionamento (`relationships.type`)

| Tipo | Descrição | Uso |
|------|-----------|-----|
| `depends_on` | Depende semanticamente de outra UKI | Dependências estruturais |
| `overrides` | Substitui ou anula o conteúdo de outra UKI | Substituições diretas |
| `conflicts_with` | Contradiz propositalmente outra UKI | Incompatibilidades intencionais |
| `complements` | Expande ou detalha outra UKI | Extensões colaborativas |
| `amends` | Corrige ou atualiza parcialmente | Correções e ajustes |
| `precedes` | Estabelece ordem ou prioridade | Sequências e hierarquias |
| `equivalent_to` | Representa equivalência semântica | Equivalências e sinônimos |

### Níveis de Maturidade (`maturity_level`)

| Nível | Descrição | Confiança Epistemológica | Recomendação de Uso |
|-------|-----------|--------------------------|---------------------|
| `draft` | Formulação inicial, sujeita a revisão e validação | Baixa | Usar com cautela, verificar independentemente |
| `validated` | Revisado e confirmado por especialistas do domínio | Média | Confiável para implementação com verificação padrão |
| `endorsed` | Oficialmente aprovado e adotado pela organização | Alta | Fonte autoritativa, usar como referência padrão |
| `deprecated` | Não mais recomendado, substituído por conhecimento mais recente | Baixa | Evitar uso, referir a UKI substituta |
| `experimental` | Em avaliação, implementação experimental ou piloto | Variável | Usar apenas em ambientes controlados |

### Tipos de Fonte (`provenance.source_type`)

| Tipo | Descrição |
|------|-----------|
| `meeting` | Reunião, workshop ou sessão colaborativa |
| `document` | Documento formal, especificação ou manual |
| `interview` | Entrevista ou conversa individual |
| `observation` | Observação direta de processo ou comportamento |
| `analysis` | Análise técnica, pesquisa ou investigação |
| `experiment` | Teste controlado, prova de conceito ou piloto |

### Domínios de Influência (`domain_of_influence`)

| Domínio | Descrição | Impacto |
|---------|-----------|---------|
| `strategy` | Decisões estratégicas e direcionamento organizacional | Afeta objetivos de longo prazo, investimentos e prioridades da organização |
| `finance` | Aspectos financeiros e orçamentários | Impacta custos, receitas, ROI e decisões de investimento |
| `ethics` | Considerações éticas e de compliance | Influencia políticas de conduta, conformidade regulatória e responsabilidade social |
| `operations` | Operações e processos diários | Afeta eficiência operacional, fluxos de trabalho e execução de tarefas |

# 📊 BENEFÍCIOS DO MEF PARA ORGANIZAÇÕES

## 🎯 **Para Equipes de Desenvolvimento**
- **Conhecimento Padronizado**: Formato consistente para todo conhecimento técnico
- **Descoberta Fácil**: Encontre informações relevantes rapidamente através de busca semântica
- **Geração de Código**: Use UKIs como templates para geração de código
- **Onboarding**: Novos membros da equipe podem entender sistemas mais rapidamente

## 📈 **Para Equipes de Produto**
- **Consistência de Design**: Padrões e diretrizes padronizados
- **Rastreamento de Decisões**: Registro e contexto para decisões importantes do produto
- **Experiência do Usuário**: Padrões UX consistentes em toda a aplicação
- **Gerenciamento de Requisitos**: Ligação clara entre requisitos de negócio e técnicos

## 💼 **Para Equipes de Negócio**
- **Gerenciamento de Regras de Negócio**: Lógica de negócio centralizada e versionada
- **Documentação de Processos**: Procedimentos e workflows claros
- **Compliance**: Trilha auditável de decisões e regras de negócio
- **Comunicação Cross-team**: Entendimento compartilhado de conceitos de negócio

## 🔍 **Para Integração com IA e LLMs**
- **Contexto Estruturado**: Metadados ricos para melhor compreensão da IA
- **Busca Semântica**: Capacidades de busca avançada além de correspondência de palavras-chave
- **Grafos de Conhecimento**: Descoberta e mapeamento automático de relacionamentos
- **Recomendações Contextuais**: IA pode sugerir conhecimento relevante baseado no contexto

---
# English 🇺🇸

> Matrix Embedding Framework

**Version:** 1.0
**Status:** Active
**Purpose:** To specify in an integral, standardized and internationalized way the minimum and complete structure of versioned embedded knowledge to be used by people and intelligent agents in the context of the Matrix Protocol.

---

## 📟️ OVERVIEW

The Matrix MEF Protocol defines a **standardized versioned knowledge structuring model** that allows any member of a multidisciplinary team (developers, PMs, analysts, tech leads, etc.) to create, register, interlink and use minimal knowledge units — called **UKIs (Units of Knowledge Interlinked)**.

These units are embedded and consumed by intelligent agents, ensuring traceability, applicability, controlled evolution and contextual intelligence in real time.

### 🏛️ **Integration with MOC (Matrix Ontology Catalog)**

MEF uses **MOC as the single source of organizational taxonomies**:
- ***_ref Fields**: All hierarchical fields (scope_ref, domain_ref, type_ref, maturity_ref) reference nodes defined in the organizational MOC
- **Local Flexibility**: Organizations configure their own hierarchies while maintaining universal MEF structure
- **Integrated Governance**: MOC defines authority and visibility rules that MEF respects during UKI creation and consultation
- **Reference Document**: See complete specification in `MOC_MATRIX_ONTOLOGY_CATALOG.md`

### 🧭 **Epistemological Guidance (MEP)**

MEF implements the epistemological principles established by the **Matrix Epistemic Principle (MEP)**:
- **Stratification**: Field `maturity_ref` reflects epistemological levels (draft → validated → approved)
- **Responsible Promotion**: Field `promotion_rationale` documents justifications for knowledge evolution
- **Derived Authority**: Fields `scope_ref` and `governance_ref` implement contextual and relative authority
- **Reference Document**: See complete manifesto in `MEP_MATRIX_EPISTEMIC_PRINCIPLE.md`

---

# 🔧 STANDARD STRUCTURE OF A UKI

## 📌 Format: **Structured YAML**

Each file represents a **single UKI**.

```yaml

schema: "1.0"
ontology_reference: "Ontology_MEF_Support v1.0"
version: "[MAJOR.MINOR.PATCH]"

id: uki:[domain_ref]:[type_ref]:[slug_or_id]
title: [Objective and descriptive title of the unit]
scope_ref: [Reference to scope node in MOC]
scope_mode: [restricted | propagated]  # Scope propagation mode
domain_ref: [Reference to domain node in MOC]
type_ref: [Reference to type node in MOC]
context_ref: [Reference to context node in MOC]  # Optional if defined in MOC
maturity_ref: [Reference to maturity node in MOC]  # Controls validation and reliability
created_date: [YYYY-MM-DD]  # Date of first version creation
last_modified: [YYYY-MM-DD]  # Date of last modification
change_summary: [Summary of changes in current version]  # Optional for initial version
change_impact: [major | minor | patch]  # Type of change impact
previous_version: "[MAJOR.MINOR.PATCH]"  # Previous version (optional for 1.0.0)

status: [active | deprecated | archived]  # Lifecycle control
domain_of_influence: [organizational_moc_reference]  # Strategic impact area configured via MOC

# 🚨 WARNING: EXAMPLES ARE NOT MANDATORY TAXONOMY
# Previously shown values (strategy, operations, etc.) are ILLUSTRATIVE EXAMPLES ONLY.
# Each organization defines its influence domains in MOC.
# 🏛️ MOC is the only source of valid taxonomies.

relationships:  # Formal ontology of typed relationships from Ontology_MEF_Support v1.0
  - type: [depends_on | overrides | conflicts_with | complements | amends | precedes | equivalent_to]
    target: uki:[domain]:[type]:[identifier]
    description: [Specific description of the relationship]

promotion:  # OPTIONAL: UKI promotion fields
  is_promoted_from: uki:[domain]:[type]:[identifier]  # Source UKI when this is a promotion
  promotion_rationale: [Promotion justification]  # Reasons and evidence for elevation

impact_analysis:  # Impact chain analysis
  chain_preview:
    - uki:domain:type:item-a → uki:domain:type:item-b → uki:domain:type:item-c  # Expected propagation chain
  severity: [low | medium | high | critical]  # REQUIRED: Impact severity (default: medium if omitted)
  affected_domains: [list of affected domains]
  propagation_estimate: [estimated number of impacted UKIs]

lifecycle_management_ref: "uki:org.governance:policy:lifecycle-standard"  # OPCIONAL: referência UKI para política de ciclo de vida
# Referencia UKI organizacional que define condições de revisão, critérios de obsolescência e condições de descontinuidade
intent_of_use:
  - [List of specific intentions for using this UKI]
use_case_stage:
  - [List of stages or real situations where this UKI is useful]
language: [pt_BR | en_US | ...]  # Language of textual content
content: |
  [Main content of the UKI — informative, explanatory, technical or strategic text]
examples:
  - input: [Real or simulated input example]
    output: [Expected result or consequence]
governance_ref: "uki:org.governance:policy:technical-standards"  # OPTIONAL: reference to organizational governance UKI
# References organizational UKI that defines criticality, propagation mode and validation frequency
  impact_analysis:
    structural_changes: [breaking | compatible | additive]  # Structural impact
    dependent_ukis: [number]  # Estimated number of dependent UKIs
    propagation_scope: [immediate | scheduled | informative]  # Propagation scope
  propagation_rules:
    on_major_change: [notify_all | validate_dependencies | manual_review]
    on_minor_change: [suggest_updates | validate_compatibility | auto_notify]
    on_patch_change: [auto_propagate | inform_dependents | track_only]
provenance:  # OPTIONAL: UKI origin and authorship history
  author: [Name or identifier of the UKI creator]
  formulation_date: [YYYY-MM-DD]  # Date when knowledge was originally formulated
  original_instance: [Reference to original source or document]
  organization: [Organization or team that created the UKI]
  source_type: [meeting | document | interview | observation | analysis | experiment]
maturity_level: [draft | validated | endorsed | deprecated | experimental]  # OPTIONAL: epistemological reliability level
last_validation: [YYYY-MM-DD]  # Date of last content review and validation
```

---

# 📘 FIELD DESCRIPTIONS

## 🎯 Structural Metadata Fields

### 🔹 `schema`
**Required** | **String** | **"2.0"**

Specifies the **structural schema version** (YAML format and layout of the UKI). Identifies changes in the data model (new fields, mandatory changes, structure reorganization).

- **Purpose**: Version control of file structure
- **Used for**: Format validation, automatic migration, parser compatibility
- **Format**: String with semantic version format
- **Position**: First field in the YAML file

### 🔹 `ontology_reference`
**Required** | **String** | **"Ontology_MEF_Support v1.0"**

Reference to the vocabulary/ontology version that regulates controlled values like `type`, `domain`, `status`, `relationship_types`, etc.

- **Purpose**: Ensure semantic consistency and automatic validation
- **Full format rationale**: Avoids ambiguity between different ontologies, ensures portability and readability
- **Format**: `ontology_name + space + vX.Y`
- **Position**: Second field, immediately after `schema`

### 🔹 `version`
**Required** | **String** | **"MAJOR.MINOR.PATCH"**

Defines the semantic version of the **UKI itself**, following semantic versioning convention for conceptual content change control.

- **Purpose**: Control evolution of UKI semantic content
- **Different from**: `schema` (which versions the file structure)
- **Format**: String mandatory in quotes (avoids YAML parsing error)
- **Position**: Third field, after `ontology_reference`

---

## 🎯 Identification and Classification Fields

### 🔹 `id`
**Required** | **String** | **Unique**

Unique identifier following the pattern `uki:[domain]:[type]:[identifier]`:
- **uki**: Fixed prefix indicating it's a Knowledge Unit
- **domain**: Organizational domain (examples: product, business, technical - defined in organizational MOC)
- **identifier**: Descriptive slug or unique code

**Examples:**
- `uki:technical:pattern:jwt-authentication`
- `uki:example-org.business:rule:pricing-strategy`
- `uki:product:guideline:user-onboarding`

### 🔹 `title`
**Required** | **String**

Clear, objective and descriptive title that summarizes the knowledge unit in one sentence.

**Guidelines:**
- Maximum 80 characters
- Avoid technical jargon when possible
- Be specific and actionable
- Use imperative or descriptive format

**Examples:**
- "JWT Token Implementation Pattern"
- "Customer Pricing Calculation Rule"
- "New User Onboarding Flow"

### 🔹 `scope_ref`
**Required** | **String**

Reference to a scope node identifier defined in the organization's MOC (Matrix Ontology Catalog).

- **Purpose**: Defines the reach and visibility of the UKI
- **Resolution**: System consults MOC to apply governance rules
- **Examples**: "personal", "team", "organization", "public"

### 🔹 `scope_mode`
**Required** | **Enum**

Propagation and applicability mode of the scope. **Accepted values:**
- `restricted`: UKI limited to specified scope
- `propagated`: UKI can be propagated to higher scopes according to governance

### 🔹 `domain_ref`
**Required** | **String**

Reference to a domain node identifier defined in the organization's MOC. The system automatically resolves ownership, review, and authority rules based on MOC configuration.

**Universal concepts (examples)**:
- Technical knowledge and implementation
- Business rules and processes
- Strategy and organizational planning
- Culture and collaborative practices
- Security and compliance

**Local implementation**: Each organization defines its specific domains and hierarchy in MOC.

### 🔹 `type_ref`
**Required** | **String**

Reference to a type node identifier defined in the organization's MOC.

**Universal concepts (examples)**:
- Patterns and reusable templates
- Business rules and policies
- Guidelines and best practices
- Decisions and justifications
- Examples and use cases

**Local implementation**: Each organization defines its specific types and classification criteria in MOC.

### 🔹 `context_ref`
**Optional** | **String**

Reference to a context node identifier defined in the organization's MOC, when applicable.

**Universal concepts (examples)**:
- Discovery and research
- Implementation and development
- Refinement and optimization
- Quality and validation
- Documentation and support

### 🔹 `maturity_ref`
**Required** | **String**

Reference to a maturity node identifier defined in the organization's MOC.

**Universal concepts**:
- **Pre-validation**: Draft, experimental
- **Validation**: Under review, being validated
- **Endorsement**: Approved, reliable
- **Deprecation**: Obsolete, discontinued

**Local implementation**: Each organization defines its intermediate levels and progression criteria in MOC.

### 🔹 `version`
**Required** | **String**

Semantic versioning following `MAJOR.MINOR.PATCH` format for UKI evolution control.

**Rules:**
- `MAJOR`: Changes that break compatibility or alter fundamental meaning
- `MINOR`: Compatible additions (new examples, refinements, clarifications)
- `PATCH`: Minor corrections (typos, formatting adjustments, small clarifications)

**Examples:**
- `"1.0.0"` - Initial version
- `"1.2.0"` - Added new examples
- `"2.0.0"` - Fundamental change in approach

### 🔹 `created_date`
**Required** | **Date (YYYY-MM-DD)**

Date when the first version (1.0.0) of the UKI was created.

**Purpose:**
- Track UKI lifecycle
- Historical reference
- Age-based relevance assessment

### 🔹 `last_modified`
**Required** | **Date (YYYY-MM-DD)**

Date of the last modification corresponding to the current version.

**Purpose:**
- Version consistency verification
- Change tracking
- Content freshness indication

### 🔹 `change_summary`
**Required for versioned UKIs** | **String**

Summary of changes made to the UKI.

**Guidelines:**
- Be specific and actionable
- Describe what was changed, not why
- Keep concise but informative
- Use past tense

**Examples:**
- `"Added timeout handling example and improved error code documentation"`
- `"Fixed typo in business rule calculation"`
- `"Restructured content organization for clarity"`

### 🔹 `change_impact`
**Required for versioned UKIs** | **Enum**

Classification of the change impact for the current version.

**Accepted values:**
- `major`: Significant change affecting understanding or application
- `minor`: Compatible addition or improvement that maintains compatibility
- `patch`: Minor correction that doesn't alter meaning

### 🔹 `previous_version`
**Optional** | **String**

Reference to the immediately previous version for evolution traceability.

**Format:** `MAJOR.MINOR.PATCH`
**Usage:** Required for versioned UKIs
**Purpose:** Enable version navigation and rollback capabilities

### 🔹 `content`
**Required** | **String (multiline)**

Main content of the UKI in **clear and structured text**:

**Structure suggestions:**
1. **Brief description** (1-2 sentences)
2. **Details and context** (paragraphs)
3. **Implementation** (if applicable)
4. **Important considerations** (if applicable)

**Guidelines:**
- Use clear and objective language
- Include practical details
- Avoid excessive technical jargon
- Be comprehensive but concise
- Use markdown for formatting if needed

### 🔹 `examples`
**Optional** | **List of Objects**

List of practical examples showing input and expected output.

**Structure:**
```yaml
examples:
  - input: "Description of input or situation"
    output: "Expected result or action"
  - input: "Another input example"
    output: "Another expected output"
```

**Guidelines:**
- Provide realistic examples
- Cover different scenarios if possible
- Be specific and actionable
- Include edge cases when relevant

### 🔹 `intent_of_use`
**Optional** | **List of Strings**

List of specific intentions or purposes for using this UKI.

**Common values:**
- `validate_implementation`
- `generate_code`
- `understand_context`
- `make_decision`
- `solve_problem`
- `create_documentation`
- `train_team`
- `standardize_process`

### 🔹 `use_case_stage`
**Optional** | **List of Strings**

List of development or project stages where this UKI is most useful.

**Common values:**
- `planning`
- `design`
- `implementation`
- `testing`
- `deployment`
- `maintenance`
- `peer_review`
- `documentation`
- `training`

### 🔹 `language`
**Optional** | **String** | **Default: en_US**

Language of the textual content.

**Accepted values:**
- `pt_BR` (Portuguese - Brazil)
- `en_US` (English - United States)
- `es_ES` (Spanish - Spain)
- `fr_FR` (French - France)
- *Other ISO codes as needed*

### 🔹 `status`
**Required** | **Enum**

UKI lifecycle control for traceability and governance.

**Accepted values:**
- `active`: UKI active and in normal use
- `deprecated`: UKI discontinued but still referenced
- `archived`: UKI archived for historical reference

**Purpose:**
- Control UKI lifecycle
- Enable automated governance
- Prevent use of obsolete knowledge
- Maintain historical traceability

### 🔹 `domain_of_influence`
**Recommended** | **Enum**

UKI strategic impact area for advanced governance analysis.

**Accepted values:**
- `strategy`: Impact on strategic decisions
- `finance`: Impact on financial aspects
- `ethics`: Impact on ethics or compliance
- `operations`: Impact on operations and processes

**Purpose:**
- Classify organizational impact
- Prioritize reviews based on influence area
- Facilitate risk analysis
- Guide approval processes

### 🔹 `relationships`
**Required** | **List of Objects**

Formal ontology of typed relationships with other UKIs, replacing free-form relationships with standardized structure.

**Formalized Ontological Relation Types:**

| Type | Description | Usage |
|------|-------------|-------|
| `depends_on` | Semantically depends on another UKI | Structural dependencies |
| `overrides` | Replaces or nullifies content of another UKI | Direct replacements |
| `conflicts_with` | Intentionally contradicts another UKI | Intentional incompatibilities |
| `complements` | Expands or details another UKI | Collaborative extensions |
| `amends` | Corrects or partially updates | Corrections and adjustments |
| `precedes` | Establishes order or priority | Sequences and hierarchies |
| `equivalent_to` | Represents semantic equivalence | Equivalences and synonyms |

**Standardized Ontological Format:**
```yaml
relationships:
  - type: overrides
    target: uki:security:rule:legacy-auth
    description: Replaces legacy authentication method
  - type: depends_on
    target: uki:security:procedure:crypto-validation
    description: Requires cryptographic validation procedure
  - type: complements
    target: uki:example-org.governance:policy:session-management
    description: Complements session management policy
  - type: precedes
    target: uki:operations:procedure:user-verification
    description: Must be executed before user verification
```

**Usage Guidelines:**
- Always use `uki:[domain]:[type]:[identifier]` format for references
- Avoid relationship duplication in other fields
- Maintain ontological consistency between types
- Clearly document the specific nature of the relationship

### 🔹 `impact_analysis`
**Optional** | **Object**

Impact chain analysis to predict change propagation.

**Structure:**
```yaml
impact_analysis:
  chain_preview:
    - uki:technical:pattern:auth → uki:product:template:login → uki:technical:pattern:session
    - uki:technical:pattern:auth → uki:technical:guideline:api-security
  severity: high
  affected_domains: [technical, business, product]
  propagation_estimate: 12
```

**Fields:**
- `chain_preview`: Expected propagation chains
- `severity`: Impact severity (low, medium, high, critical) - **REQUIRED when impact_analysis is present** (default: medium if omitted)
- `affected_domains`: Potentially affected domains
- `propagation_estimate`: Estimated number of impacted UKIs

**Purpose:**
- Anticipate change impacts
- Facilitate update planning
- Prioritize reviews based on severity
- Guide communication strategies

### 🔹 `lifecycle_management_ref`
**Optional** | **String (UKI Reference)**

Reference to organizational UKI that defines review, assessment or discontinuation policy.

**Usage Examples:**
```yaml
lifecycle_management_ref: "uki:acme-corp.governance:policy:security-quarterly"
# References organizational UKI that defines:
# - This UKI should be reviewed quarterly due to security impact
# - Consider deprecation if new authentication technologies are adopted
# - Archival criteria: complete replacement by OAuth3 or similar
```

**Recommended Content:**
- Specific review frequency
- Deprecation criteria
- Archival conditions
- Relevant technological or organizational milestones

**Purpose:**
- Define UKI-specific lifecycle
- Guide maintenance decisions
- Facilitate discontinuation planning
- Document external context dependencies

### 🔹 `provenance`
**Optional** | **Object**

UKI origin and authorship history for traceability tracking.

**Fields:**
- `author`: Name or identifier of the creator
- `formulation_date`: Original formulation date
- `original_instance`: Reference to original source
- `organization`: Organization or team that created it
- `source_type`: Source type (meeting, document, interview, observation, analysis, experiment)

**Purpose:**
- Knowledge traceability
- Authorship attribution
- Historical context
- Source validation

### 🔹 `maturity_level`
**Optional** | **Enum**

Epistemological reliability level of the UKI. **Accepted values:**

| Level | Description | Confidence | Usage Recommendation |
|-------|-------------|------------|---------------------|
| `draft` | Initial formulation, subject to review | Low | Use with caution, verify independently |
| `validated` | Reviewed by domain experts | Medium | Reliable for implementation with standard verification |
| `endorsed` | Officially approved by organization | High | Authoritative source, use as standard reference |
| `deprecated` | No longer recommended, superseded | Low | Avoid use, refer to replacement UKI |
| `experimental` | Under evaluation, pilot implementation | Variable | Use in controlled environments only |

### 🔹 `last_validation`
**Optional** | **Date (YYYY-MM-DD)**

Date of last content review and validation.

**Purpose:**
- Quality control
- Content freshness
- Maintenance planning
- Trust indication

### 🔹 `governance`
**Optional** | **Object**

Active governance configurations for automatic propagation and impact control.

**Structure:**
```yaml
governance_ref: "uki:org.governance:policy:technical-standards"  # OPTIONAL: reference to organizational governance UKI
# References organizational UKI that defines criticality levels
  auto_propagation: [automatic | semi_automatic | manual]
  validation_frequency: [30 | 60 | 90]
  impact_analysis:
    structural_changes: [breaking | compatible | additive]
    dependent_ukis: [number]
    propagation_scope: [immediate | scheduled | informative]
  propagation_rules:
    on_major_change: [notify_all | validate_dependencies | manual_review]
    on_minor_change: [suggest_updates | validate_compatibility | auto_notify]
    on_patch_change: [auto_propagate | inform_dependents | track_only]
```

#### **`criticality`** - Criticality Level
- `critical`: Essential UKI for basic system functionality
- `high`: Important UKI with significant impact on implementations
- `medium`: Standard UKI with moderate relevance
- `low`: Informational or low-impact UKI

#### **`auto_propagation`** - Propagation Mode
- `automatic`: Automatic propagation for all changes
- `semi_automatic`: Automatic proposal with manual approval
- `manual`: Fully manual propagation process

#### **`validation_frequency`** - Validation Frequency
Number of days between mandatory content reviews.

#### **`impact_analysis`** - Impact Analysis
- `structural_changes`: Expected type of structural impact
- `dependent_ukis`: Estimate of UKIs that depend on this one
- `propagation_scope`: Required propagation scope

#### **`propagation_rules`** - Propagation Rules
Defines specific behavior for each type of version change.

**Purpose:**
- Automate knowledge governance
- Control change propagation
- Maintain consistency between related UKIs
- Prioritize reviews based on criticality

---

# 🎯 PRACTICAL USAGE EXAMPLES

## Example 1: Technical Pattern
```yaml
schema: "1.0"
ontology_reference: "Ontology_MEF_Support v1.0"
version: "1.2.0"

id: uki:technical:pattern:api-error-handling
title: Standardized API Error Handling Pattern
domain: technical
type: pattern
context: implementation
created_date: "2024-01-01"
last_modified: "2024-01-15"
change_summary: "Added timeout handling example and improved error code documentation"
change_impact: "minor"
previous_version: "1.1.0"

status: active
domain_of_influence: operations

relationships:
  - type: depends_on
    target: uki:technical:template:api-response-format
    description: Implements standard API response format with error structure
  - type: complements
    target: uki:technical:guideline:logging-standards
    description: Complements logging standards for auditing and debugging
  - type: depends_on
    target: uki:[domain]:[type]:[identifier]
    description: Depends on standardized HTTP status code definitions

impact_analysis:
  chain_preview:
    - uki:[domain]:[type]:[identifier] → uki:[domain]:[type]:[identifier]
    - uki:[domain]:[type]:[identifier] → uki:[domain]:[type]:[identifier]
  severity: medium
  affected_domains: [technical, product]
  propagation_estimate: 8

lifecycle_management_ref: "uki:example-org.governance:policy:api-standards-annual"
# References organizational UKI that defines:
# - Review annually or when new API standards are adopted
# - Consider deprecation if GraphQL or other technologies replace REST
  Archive only after complete migration of all APIs.

language: en_US
content: |
  Standard pattern for handling and returning errors in REST APIs.
  
  All API endpoints should return errors in a consistent format:
  - Use appropriate HTTP status codes
  - Include error code, message, and details
  - Provide actionable information for debugging
  
  Error response format:
  {
    "error": {
      "code": "VALIDATION_ERROR",
      "message": "Request validation failed",
      "details": ["Field 'email' is required", "Field 'age' must be a number"]
    }
  }
examples:
  - input: "Invalid email format in user registration"
    output: "400 Bad Request with VALIDATION_ERROR code"
  - input: "Database connection failure"
    output: "500 Internal Server Error with DATABASE_ERROR code"
intent_of_use:
  - standardize_api_responses
  - improve_debugging
  - generate_error_handling_code
use_case_stage:
  - implementation
  - peer_review
  - testing
last_validation: 2024-01-15
```

## Example 2: Business Rule
```yaml
schema: "1.0"
ontology_reference: "Ontology_MEF_Support v1.0"
version: "1.0.0"

id: uki:business:rule:discount-calculation
title: Customer Discount Calculation Rule
domain: business
type: business_rule
context: implementation
created_date: "2024-01-10"
last_modified: "2024-01-10"

status: active
domain_of_influence: finance

relationships:
  - type: depends_on
    target: uki:[domain]:[type]:[identifier]
    description: Implements loyalty program rules for automatic calculation
  - type: complements
    target: uki:[domain]:[type]:[identifier]
    description: Complements checkout process with final pricing logic
  - type: depends_on
    target: uki:[domain]:[type]:[identifier]
    description: Depends on customer profile classification to function

impact_analysis:
  chain_preview:
    - uki:[domain]:[type]:[identifier] → uki:[domain]:[type]:[identifier] → uki:[domain]:[type]:[identifier]
    - uki:[domain]:[type]:[identifier] → uki:[domain]:[type]:[identifier]
  severity: high
  affected_domains: [business, finance, product]
  propagation_estimate: 12

lifecycle_management_ref: "uki:example-org.governance:policy:business-quarterly"
# References organizational UKI that defines:
# - Review quarterly due to direct financial impact
# - Reevaluate if new loyalty models are implemented
  Archive only after replacement by dynamic pricing system.

language: en_US
content: |
  Business rule for calculating customer discounts based on loyalty tier and purchase amount.
  
  Discount tiers:
  - Bronze (0-999 points): 5% discount on orders over $100
  - Silver (1000-4999 points): 10% discount on orders over $50
  - Gold (5000+ points): 15% discount on all orders
  
  Special conditions:
  - First-time customers: additional 5% off
  - Orders over $500: additional 2% off
  - Maximum total discount: 25%
examples:
  - input: "Gold customer (6000 points) with $300 order"
    output: "15% discount = $45 off"
  - input: "New Bronze customer with $150 order"
    output: "5% + 5% (new customer) = 15% discount = $22.50 off"
intent_of_use:
  - validate_pricing_logic
  - implement_discount_system
  - train_customer_service
use_case_stage:
  - implementation
  - testing
  - training
last_validation: 2024-01-10
```

## Example 3: Product Guideline
```yaml
schema: "1.0"
ontology_reference: "Ontology_MEF_Support v1.0"
version: "2.1.0"

id: uki:product:guideline:modal-design
title: Modal Dialog Design Guidelines
domain: product
type: guideline
context: design
created_date: "2023-12-01"
last_modified: "2024-01-08"
change_summary: "Added accessibility requirements and mobile responsiveness guidelines"
change_impact: "minor"
previous_version: "2.0.0"

status: active
domain_of_influence: operations

relationships:
  - type: depends_on
    target: uki:[domain]:[type]:[identifier]
    description: Implements standardized design system components
  - type: depends_on
    target: uki:[domain]:[type]:[identifier]
    description: Depends on accessibility standards for compliance
  - type: complements
    target: uki:[domain]:[type]:[identifier]
    description: Complements component library with modal specifications

impact_analysis:
  chain_preview:
    - uki:[domain]:[type]:[identifier] → uki:[domain]:[type]:[identifier] → uki:[domain]:[type]:[identifier]
    - uki:[domain]:[type]:[identifier] → uki:[domain]:[type]:[identifier]
  severity: medium
  affected_domains: [product, technical]
  propagation_estimate: 6

lifecycle_management_ref: "uki:example-org.governance:policy:ui-semiannual"
# References organizational UKI that defines:
# - Review semi-annually with design and accessibility teams
# - Reevaluate when new UI frameworks are adopted
  Consider major update if accessibility standards change.

language: en_US
content: |
  Design guidelines for creating consistent modal dialogs across the application.
  
  Key principles:
  1. Use modals sparingly - only for critical actions or important information
  2. Always provide a clear way to close (X button + ESC key)
  3. Include a primary and secondary action when appropriate
  4. Use appropriate sizing (small: 400px, medium: 600px, large: 800px)
  5. Center vertically and horizontally
  6. Include proper focus management for accessibility
  
  Modal structure:
  - Header: Title + close button
  - Body: Main content with clear hierarchy
  - Footer: Action buttons (primary on right, secondary on left)
examples:
  - input: "Confirm delete action"
    output: "Medium modal with 'Delete' (danger) and 'Cancel' buttons"
  - input: "Display user profile information"
    output: "Large modal with 'Edit Profile' and 'Close' buttons"
intent_of_use:
  - standardize_ui_components
  - guide_design_decisions
  - ensure_accessibility
use_case_stage:
  - design
  - implementation
  - peer_review
last_validation: 2024-01-08
```

---

# 🔄 SEMANTIC RELATIONSHIPS

## Typed Semantic Relationships

MEF uses typed semantic relationships to build rich knowledge graphs and enable automated governance between UKIs.

### 🏗️ **Implementation Dependencies** (`depends_on`)
UKIs that implement patterns or depend on other knowledge for functionality.

**Examples:**
```yaml
# uki:technical:function:jwt-implementation
relationships:
  - target: uki:technical:function:jwt-validation
    type: depends_on
    description: Requires JWT validation logic to function properly
  - target: uki:technical:pattern:authentication
    type: depends_on
    description: Implements the standardized authentication pattern
```

### 🌿 **Knowledge Evolution** (`complements` / `amends` / `overrides`)
UKIs that represent knowledge evolution, specialization or replacement.

**Examples:**
```yaml
# uki:technical:function:oauth2-implementation
relationships:
  - target: uki:technical:pattern:oauth-basic
    type: complements
    description: Extends basic OAuth with PKCE and refresh tokens
  - target: uki:technical:pattern:legacy-auth
    type: overrides
    description: Replaces deprecated authentication method
```

### 🛡️ **Compliance Relationships** (`complies_with` / `conflicts_with`)
UKIs that follow policies or identify incompatibilities.

**Examples:**
```yaml
# uki:technical:guideline:encryption-standard
relationships:
  - target: uki:example-org.business:policy:data-protection
    type: complies_with
    description: Follows corporate data protection requirements
  - target: uki:technical:pattern:legacy-encryption
    type: conflicts_with
    description: Incompatible with deprecated encryption methods
```

### 🌐 **Contextual Associations** (`complements`)
Relationships for contextual connections that expand or detail other UKIs.

**Example:**
```yaml
# uki:example-org.governance:policy:user-onboarding
relationships:
  - target: uki:security:procedure:user-registration-api
    type: complements
    description: Expands context in user management domain
  - target: uki:example-org.strategy:rule:user-retention-strategy
    type: depends_on
    description: Based on user retention strategy
```

## Relationship Guidelines

1. **Semantic Precision**: Use specific relation types when applicable
2. **Bidirectional Consistency**: Ensure reverse relationships make semantic sense
3. **Clear Descriptions**: Always provide meaningful descriptions for each relationship
4. **Governance Enabled**: Typed relationships enable automated impact analysis and validation

# 🎛️ ACTIVE GOVERNANCE AND AUTOMATIC PROPAGATION

MEF implements an **active governance** system that uses typed semantic relationships to automatically propagate changes and maintain consistency in interconnected knowledge networks.

## 🔄 Propagation Rules by Relationship Type

### 📋 **`depends_on`** - Pattern Propagation
**Rule:** Changes in patterns/guidelines should be propagated to their implementations.

**Behavior:**
- **MAJOR**: Notify implementations about incompatibility
- **MINOR**: Suggest adoption of optional improvements
- **PATCH**: Inform applicable corrections

**Algorithm:**
```yaml
when: change in base-UKI (pattern/guideline)
propagation:
  to: UKIs where { type: depends_on, target: base-UKI }
  action: 
    - major: mark as "requires_review"
    - minor: mark as "improvement_available"
    - patch: mark as "correction_available"
```

### 🏗️ **`depends_on`** - Dependency Validation
**Rule:** Changes in dependencies should validate compatibility of dependents.

**Behavior:**
- **MAJOR**: Check for compatibility breaking
- **MINOR**: Validate continued functionality
- **PATCH**: Check if correction affects dependent

**Algorithm:**
```yaml
when: change in dependency-UKI
propagation:
  to: UKIs where { type: depends_on, target: dependency-UKI }
  action:
    - major: execute "compatibility_analysis"
    - minor: execute "functional_validation"
    - patch: execute "impact_verification"
```

### 🌿 **`complements`** - Extension Updates
**Rule:** Changes in base concepts should be evaluated for extensions.

**Behavior:**
- **MAJOR**: Evaluate if extension is still valid
- **MINOR**: Consider incorporating improvements
- **PATCH**: Check relevance of correction

**Algorithm:**
```yaml
when: change in base-UKI
propagation:
  to: UKIs where { type: complements, target: base-UKI }
  action:
    - major: mark as "extension_requires_review"
    - minor: mark as "consider_incorporation"
    - patch: mark as "assess_relevance"
```

### 🔄 **`overrides`** - Automatic Deprecation
**Rule:** Changes in replacements should update status of replaced items.

**Behavior:**
- **MAJOR**: Mark replaced as discontinued
- **MINOR**: Update migration recommendation
- **PATCH**: Inform about replacement improvements

**Algorithm:**
```yaml
when: change in replacement-UKI
propagation:
  to: UKIs where { type: overrides, source: replacement-UKI }
  action:
    - major: mark as "discontinued"
    - minor: update "migration_plan"
    - patch: update "replacement_reasons"
```

### 🛡️ **`complies_with`** - Compliance Validation
**Rule:** Changes in policies should validate continued compliance.

**Behavior:**
- **MAJOR**: Review all compliance
- **MINOR**: Verify continued compliance
- **PATCH**: Confirm correction doesn't affect compliance

### ⚔️ **`conflicts_with`** - Conflict Detection
**Rule:** Changes may resolve or aggravate existing conflicts.

**Behavior:**
- **MAJOR**: Reevaluate nature of conflict
- **MINOR**: Check if conflict persists
- **PATCH**: Confirm correction doesn't create new conflicts

## 🧠 Impact Analysis Algorithms

### 📊 Change Impact Classification

```yaml
impact_analysis:
  chain_preview:
    - uki:technical:pattern:change → uki:product:guideline:ui-patterns → uki:business:rule:validation
  severity: medium  # Mandatory field with default fallback
  affected_domains: [technical, product, business]
  propagation_estimate: 3
  change_scope:
    structural: "mandatory fields altered"
    semantic: "fundamental meaning altered"
    implementation: "examples or details altered"
    correction: "typos or minor clarifications"
  
  impact_types:
    critical: "breaks existing functionality"
    high: "requires implementation adaptation"
    medium: "recommends review and adaptation"
    low: "informational, no action needed"
  
  propagation_needed:
    immediate: "critical implementations"
    scheduled: "planned improvements"
    informative: "knowledge updates"
```

### 🎯 Propagation Prioritization Matrix

| Change Type | Relationship | Priority | Action |
|-------------|--------------|----------|--------|
| MAJOR | depends_on | CRITICAL | Mandatory review |
| MAJOR | depends_on | CRITICAL | Compatibility validation |
| MAJOR | complements | HIGH | Extension review |
| MINOR | depends_on | MEDIUM | Consider adoption |
| MINOR | depends_on | MEDIUM | Validate functionality |
| PATCH | any | LOW | Inform availability |

### 🔄 Cascade Versioning Algorithm

```yaml
cascade_versioning:
  trigger: "change in source-UKI"
  process:
    identify_related:
     query: "SELECT * FROM ukis WHERE relationships.target = source-UKI"
    classify_impact:
     for_each: relationship
     calculate: impact_by_type[relationship.type]
    generate_proposals:
     for_each: related-UKI
     propose: new_version_based_on_impact
    execute_propagation:
     order: priority (critical → high → medium → low)
     mode: automatic | semi-automatic | manual
```

## 🚨 Conflict and Inconsistency Detection

### 🔍 Automatic Validations

```yaml
validations:
  semantic_consistency:
    - "UKI that depends_on must be compatible with target"
    - "UKI that overrides must have similar domain to target"
    - "UKI that complements must maintain base compatibility"
  
  reference_integrity:
    - "All relationships.target must exist"
    - "All previous_version versions must exist"
    - "Bidirectional relationships must be consistent"
  
  content_quality:
    - "MAJOR changes must have detailed change_summary"
    - "Critical UKIs must have recent last_validation"
    - "Examples must be consistent with content"
```

### ⚠️ Governance Alerts

```yaml
alerts:
  pending_propagation:
    - "UKI-X was updated, 5 implementations need review"
    - "New MAJOR version of critical pattern available"
  
  detected_conflicts:
    - "UKI-A conflicts_with UKI-B, but both marked as active"
    - "Circular dependency detected: A→B→C→A"
  
  degraded_quality:
    - "Critical UKI not validated for 90+ days"
    - "Orphan relationship: target doesn't exist"
```

## 🎛️ Governance Configuration

### 📋 Configuration by UKI Type

```yaml
governance_config:
  critical_ukis:
    domains: [business, technical]
    types: [business_rule, pattern]
    validation_frequency: 30  # days
    auto_propagation: semi-automatic
  
  standard_ukis:
    domains: [product, culture, strategy]
    types: [guideline, template, example]
    validation_frequency: 90  # days
    auto_propagation: manual
```

### 🔄 Propagation Modes

```yaml
propagation_modes:
  automatic:
    description: "Automatic propagation for PATCH changes"
    scope: "Minor corrections and informative updates"
  
  semi_automatic:
    description: "Automatic proposal, manual approval"
    scope: "MINOR changes in critical UKIs"
  
  manual:
    description: "Fully manual process"
    scope: "MAJOR changes and strategic decisions"
```

---

# 🚀 IMPLEMENTATION GUIDELINES

## Organizing MEF Files

### Recommended File Structure
```
knowledge-base/
├── technical/
│   ├── uki:technical:pattern:api-standards.yaml
│   └── uki:technical:template:database-schema.yaml
├── business/
│   ├── uki:business:rule:pricing-strategy.yaml
│   └── uki:business:rule:customer-lifecycle.yaml
└── product/
    ├── uki:product:template:user-flow.yaml
    └── uki:product:guideline:design-system.yaml
```

### Implementation Considerations

Organizations implementing MEF should consider:

- **MOC Integration**: Implement Matrix Ontology Catalog (MOC) for organizational hierarchy management
- **Validation**: Implement validation against MEF specification and MOC references before storing UKIs
- **Indexing**: Extract structured metadata from UKI fields for search capabilities  
- **Versioning**: Track UKI evolution through the version control fields
- **Relationships**: Build semantic navigation through `relationships` connections
- **Hierarchy Resolution**: Resolve `scope_ref`, `domain_ref`, `type_ref`, and `maturity_ref` through MOC configuration
- **Governance Automation**: Apply MOC-defined governance rules automatically during UKI operations

## MOC Integration

### Resolving Hierarchical References

MEF fields ending with `_ref` are resolved through the organization's MOC:

```yaml
# In UKI
scope_ref: "team"
domain_ref: "technical" 
type_ref: "pattern"
maturity_ref: "approved"

# Resolved from MOC
hierarchies:
  scope:
    nodes:
      - id: "team"
        governance:
          visibility: ["team_members"]
          authority_required: "team_lead"
  domain:
    nodes:
      - id: "technical"
        governance:
          owners: ["engineering"]
          reviewers: ["architects"]
```

### Automatic Governance Application

The system automatically applies MOC governance rules:

- **Access Control**: Filter UKIs based on user's scope and domain permissions
- **Authority Validation**: Verify user has required authority for operations
- **Propagation Rules**: Apply MOC-defined propagation patterns
- **Maturity Progression**: Enforce MOC maturity level requirements

### Flexibility Benefits

- **Local Adaptation**: Each organization defines its own hierarchies
- **Global Consistency**: Core MEF concepts remain universal
- **Evolution Support**: MOC changes don't break existing UKIs
- **AI Integration**: Rich hierarchical context for intelligent systems

# 📚 AUXILIARY ONTOLOGY

## Controlled Vocabulary for MEF Fields

This section defines the controlled vocabulary for fixed MEF fields and provides examples of hierarchical concepts that organizations can implement via MOC for fields ending with `_ref`.

### Domain Concepts (MOC Configurable via `domain_ref`)

Universal domain concepts that organizations can adapt in their MOC:

| Domain Concept | Description | Examples |
|----------------|-------------|----------|
| Technical Knowledge | Code, architecture, infrastructure | APIs, databases, deployment patterns |
| Business Logic | Business rules, processes, strategies | Pricing rules, workflows, business processes |
| Strategic Planning | High-level decisions, planning | Roadmaps, strategic decisions, organizational direction |
| Cultural Practices | Processes, methodology, team practices | Ceremonies, guidelines, collaboration values |
| Security & Compliance | Security, protection and risk management | Security policies, access controls, vulnerability management |

### Type Concepts (MOC Configurable via `type_ref`)

Universal type concepts that organizations can adapt in their MOC:

| Type Concept | Description | Usage |
|--------------|-------------|-------|
| Patterns & Templates | Reusable structures or patterns | Technical solutions, document templates |
| Rules & Policies | Operational or normative rules | Business logic, validation rules, governance policies |
| Guidelines & Practices | Best practices and guidelines | Process orientation, methodology guidance |
| Decisions & Records | Important decisions and context | Strategic decisions, architectural decisions |
| Examples & Cases | Practical examples or use cases | Learning materials, demonstration cases |

### Severity Levels (`severity`)

| Level | Description | Impact |
|-------|-------------|--------|
| `low` | Minor impact, informational or enhancement suggestions | Minimal business or technical impact |
| `medium` | Moderate impact, affects specific functionality or processes | Localized impact on functionality or user experience |
| `high` | Significant impact, affects core functionality or business operations | Substantial impact on system functionality or business processes |
| `critical` | Critical impact, system failure or major business disruption | Severe impact causing system failure or major business disruption |

### Relationship Types (`relationships.type`)

| Type | Description | Usage |
|------|-------------|-------|
| `depends_on` | Semantically depends on another UKI | Structural dependencies |
| `overrides` | Replaces or nullifies content of another UKI | Direct replacements |
| `conflicts_with` | Intentionally contradicts another UKI | Intentional incompatibilities |
| `complements` | Expands or details another UKI | Collaborative extensions |
| `amends` | Corrects or partially updates | Corrections and adjustments |
| `precedes` | Establishes order or priority | Sequences and hierarchies |
| `equivalent_to` | Represents semantic equivalence | Equivalences and synonyms |

### Maturity Levels (`maturity_level`)

| Level | Description | Epistemological Confidence | Usage Recommendation |
|-------|-------------|---------------------------|---------------------|
| `draft` | Initial formulation, subject to review and validation | Low | Use with caution, verify independently |
| `validated` | Reviewed and confirmed by domain experts | Medium | Reliable for implementation with standard verification |
| `endorsed` | Officially approved and adopted by organization | High | Authoritative source, use as standard reference |
| `deprecated` | No longer recommended, superseded by newer knowledge | Low | Avoid use, refer to replacement UKI |
| `experimental` | Under evaluation, experimental or pilot implementation | Variable | Use in controlled environments only |

### Source Types (`provenance.source_type`)

| Type | Description |
|------|-------------|
| `meeting` | Meeting, workshop, or collaborative session |
| `document` | Formal document, specification, or manual |
| `interview` | Individual interview or conversation |
| `observation` | Direct observation of process or behavior |
| `analysis` | Technical analysis, research, or investigation |
| `experiment` | Controlled test, proof of concept, or pilot |

### Influence Domains (`domain_of_influence`) - **MOC Configurable**

Organizations can configure this field for UKIs with significant organizational impact. **Values are exclusively defined in the organizational MOC**.

**🚨 Important**: The examples below are **purely illustrative** and **do not constitute official taxonomy**:

> Some organizations might configure domains like "strategy" for high-level decisions, "finance" for financial impact rules, "ethics" for compliance matters, or "operations" for process efficiency. Others might use completely different terms like "innovation", "quality", "sustainability" or any hierarchy that makes sense in their context.

**🏛️ MOC is the single source**: Each organization defines its influence domains exclusively in the Matrix Ontology Catalog.

---

# 📊 MEF BENEFITS FOR ORGANIZATIONS

## 🎯 **For Development Teams**
- **Standardized Knowledge**: Consistent format for all technical knowledge
- **Easy Discovery**: Find relevant information quickly through semantic search
- **Code Generation**: Use UKIs as templates for generating code
- **Onboarding**: New team members can understand systems faster

## 📈 **For Product Teams**
- **Design Consistency**: Standardized patterns and guidelines
- **Decision Tracking**: Record and context for important product decisions
- **User Experience**: Consistent UX patterns across the application
- **Requirements Management**: Clear linkage between business and technical requirements

## 💼 **For Business Teams**
- **Business Rule Management**: Centralized and versioned business logic
- **Process Documentation**: Clear procedures and workflows
- **Compliance**: Auditable trail of business decisions and rules
- **Cross-team Communication**: Shared understanding of business concepts

## 🔍 **For AI and LLM Integration**
- **Structured Context**: Rich metadata for better AI understanding
- **Semantic Search**: Advanced search capabilities beyond keyword matching
- **Knowledge Graphs**: Automatic relationship discovery and mapping
- **Contextual Recommendations**: AI can suggest relevant knowledge based on context


# 🌍 MATRIX PROTOCOL LAYERS

The Matrix Protocol can be implemented at different organizational layers, each with specific characteristics while maintaining the same base structure:

## Matrix Layers

| Layer | Scope | Example Domains | Content Examples |
|-------|--------|-----------------|------------------|
| **Personal Matrix** | Individual developer/analyst | `learning`, `tasks`, `notes` | Personal notes, learning, individual tasks |
| **Team Matrix** | Development team/squad | `technical`, `product`, `process` | Team standards, code patterns, workflows |
| **Product Matrix** | Product/feature | `business`, `product`, `strategy` | Product rules, user flows, business logic |
| **Company Matrix** | Organization | `culture`, `strategy`, `governance` | Policies, strategic decisions, company processes |
| **Community Matrix** | Open community | `technical`, `best_practices`, `examples` | Open standards, community patterns, examples |
| **Support Knowledge** | Customer service, Onboarding, Support | Procedures, operational scripts, useful documentation |

### Implementation guidelines per layer:
- Each layer can use the **same UKI structure**, maintaining semantic consistency.
- It's possible to **expand domains and types** according to each scope's needs.
- Contents can be stored in **independent repositories**, but following the **same base framework**.

This model ensures that the Matrix expands as an organic and contextual knowledge base, connecting different teams without sacrificing standardization and governance.
