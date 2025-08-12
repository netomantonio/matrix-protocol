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

---

# 🔧 ESTRUTURA PADRÃO DE UMA UKI

## 📌 Formato: **YAML estruturado**

Cada arquivo representa uma **única UKI**.

```yaml
id: unik-[domain]-[slug_or_id]
title: [Título objetivo e descritivo da unidade]
domain: [product | business | technical | strategy | culture]
type: [business_rule | function | template | guideline | pattern | decision | example]
context: [discovery | implementation | refinement | qa | documentation | support]
version: [MAJOR.MINOR.PATCH]  # Versionamento semântico da UKI
created_date: [YYYY-MM-DD]  # Data de criação da primeira versão
last_modified: [YYYY-MM-DD]  # Data da última modificação
change_summary: [Resumo das mudanças na versão atual]  # Opcional para versão 1.0.0
change_impact: [major | minor | patch]  # Tipo de impacto da mudança
previous_version: [MAJOR.MINOR.PATCH]  # Versão anterior (opcional para 1.0.0)
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
related_to:
  - unik-[id de outras UKIs relacionadas semanticamente]
last_validation: [YYYY-MM-DD]  # Data da última revisão e validação de conteúdo
```

---

# 📘 DESCRIÇÃO DOS CAMPOS

### 🔹 `id`
**Obrigatório** | **String** | **Único**

Identificador único seguindo o padrão `unik-[domain]-[identifier]`:
- **unik**: Prefixo fixo indicando uma Unidade de Conhecimento
- **domain**: Um dos domínios aceitos (product, business, technical, strategy, culture)
- **identifier**: Slug descritivo ou código único

**Exemplos:**
- `unik-technical-jwt-authentication`
- `unik-business-pricing-strategy`
- `unik-product-user-onboarding`

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

### 🔹 `domain`
**Obrigatório** | **Enum**

Classificação do domínio de conhecimento. **Valores aceitos:**

| Domínio | Descrição | Exemplos |
|---------|-----------|----------|
| `product` | Funcionalidades do produto, UX/UI, fluxos do usuário | Interfaces, jornadas do usuário, features |
| `business` | Regras de negócio, processos, estratégias | Precificação, políticas, processos de negócio |
| `technical` | Código, arquitetura, infraestrutura | APIs, bancos de dados, deployment |
| `strategy` | Decisões de alto nível, planejamento | Roadmaps, decisões estratégicas |
| `culture` | Processos, metodologia, práticas da equipe | Cerimônias, diretrizes, valores |

### 🔹 `type`
**Obrigatório** | **Enum**

Classificação funcional do conteúdo. **Valores aceitos:**

| Tipo | Descrição | Uso |
|------|-----------|-----|
| `business_rule` | Regra de negócio ou restrição | Validação, lógica de decisão |
| `function` | Função ou procedimento reutilizável | Implementação de código |
| `template` | Estrutura ou padrão reutilizável | Criação de documentos, padronização |
| `guideline` | Diretriz ou boa prática | Orientação de processos |
| `pattern` | Padrão de design ou arquitetural | Soluções técnicas |
| `decision` | Registro de decisão importante | Contexto e justificativa |
| `example` | Exemplo prático ou caso de uso | Aprendizado, demonstração |

### 🔹 `context`
**Obrigatório** | **Enum**

Contexto de desenvolvimento ou uso. **Valores aceitos:**

| Contexto | Descrição | Quando usar |
|----------|-----------|-------------|
| `discovery` | Pesquisa, análise, requisitos | Fases iniciais do projeto |
| `implementation` | Desenvolvimento, construção | Desenvolvimento ativo |
| `refinement` | Melhoria, otimização | Manutenção e evolução |
| `qa` | Qualidade, testes, validação | Garantia de qualidade |
| `documentation` | Documentação, compartilhamento de conhecimento | Documentação e treinamento |
| `support` | Suporte, manutenção, operação | Pós-produção |

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
**Obrigatório para versões > 1.0.0** | **String**

Resumo claro das mudanças implementadas na versão atual.

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
**Obrigatório para versões > 1.0.0** | **Enum**

Classificação do impacto da mudança para a versão atual.

**Valores aceitos:**
- `major`: Mudança significativa que afeta compreensão ou aplicação
- `minor`: Adição ou melhoria compatível que mantém compatibilidade
- `patch`: Correção menor que não altera o significado

### 🔹 `previous_version`
**Opcional** | **String**

Referência à versão imediatamente anterior para rastreabilidade de evolução.

**Formato:** `MAJOR.MINOR.PATCH`
**Uso:** Obrigatório apenas para versões > 1.0.0
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

### 🔹 `related_to`
**Opcional** | **Lista de Strings**

Lista de IDs de outras UKIs que são semanticamente relacionadas.

**Diretrizes:**
- Usar IDs completos (`unik-domain-identifier`)
- Criar redes semânticas
- Evitar conexões excessivas
- Priorizar relacionamentos diretos

**Exemplos:**
```yaml
related_to:
  - unik-technical-oauth-implementation
  - unik-business-user-authentication-policy
  - unik-product-login-flow
```

### 🔹 `last_validation`
**Opcional** | **Data (YYYY-MM-DD)**

Data da última revisão e validação do conteúdo.

**Propósito:**
- Controle de qualidade
- Atualização do conteúdo
- Planejamento de manutenção
- Indicação de confiabilidade

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
- **Conversão para UKI:**
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

- Toda UKI deve ser modular, clara e versionada adequadamente.
- Relacionamentos entre UKIs são essenciais para navegação semântica e raciocínio dos agentes.
- Os campos `intent_of_use` e `use_case_stage` são obrigatórios e são chave para inteligência contextual.
- `language` ajuda agentes a priorizar, traduzir ou adaptar sugestões.
- Sempre que possível, utilizar sintaxe `mermaid` para diagramas textuais.
- Versionamento semântico garante evolução controlada e rastreabilidade do conhecimento.
- Iniciar sempre com versão 1.0.0 para novas UKIs.
- Incrementar MAJOR para mudanças que alterem significativamente o significado ou aplicação.
- Incrementar MINOR para adições compatíveis (novos exemplos, refinamentos, clarificações).
- Incrementar PATCH para correções menores (typos, ajustes de formatação, pequenas clarificações).
- Sempre documentar mudanças no campo `change_summary` para versões posteriores à 1.0.0.
- Manter rastreabilidade através do campo `previous_version`.
- Considerar impacto em UKIs relacionadas ao fazer mudanças significativas.

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

<a name="english"></a>
# English 🇺🇸

> Matrix Embedding Framework

**Version:** 1.0
**Status:** Active
**Purpose:** To specify in an integral, standardized and internationalized way the minimum and complete structure of versioned embedded knowledge to be used by people and intelligent agents in the context of the Matrix Protocol.

---

## 📟️ OVERVIEW

The Matrix MEF Protocol defines a **standardized versioned knowledge structuring model** that allows any member of a multidisciplinary team (developers, PMs, analysts, tech leads, etc.) to create, register, interlink and use minimal knowledge units — called **UKIs (Units of Knowledge Interlinked)**.

These units are embedded and consumed by intelligent agents, ensuring traceability, applicability, controlled evolution and contextual intelligence in real time.

---

# 🔧 STANDARD STRUCTURE OF A UKI

## 📌 Format: **Structured YAML**

Each file represents a **single UKI**.

```yaml
id: unik-[domain]-[slug_or_id]
title: [Objective and descriptive title of the unit]
domain: [product | business | technical | strategy | culture]
type: [business_rule | function | template | guideline | pattern | decision | example]
context: [discovery | implementation | refinement | qa | documentation | support]
version: [MAJOR.MINOR.PATCH]  # Semantic versioning of the UKI
created_date: [YYYY-MM-DD]  # Date of first version creation
last_modified: [YYYY-MM-DD]  # Date of last modification
change_summary: [Summary of changes in current version]  # Optional for version 1.0.0
change_impact: [major | minor | patch]  # Type of change impact
previous_version: [MAJOR.MINOR.PATCH]  # Previous version (optional for 1.0.0)
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
related_to:
  - unik-[id of other semantically related UKIs]
last_validation: [YYYY-MM-DD]  # Date of last content review and validation
```

---

# 📘 FIELD DESCRIPTIONS

### 🔹 `id`
**Required** | **String** | **Unique**

Unique identifier following the pattern `unik-[domain]-[identifier]`:
- **unik**: Fixed prefix indicating it's a Knowledge Unit
- **domain**: One of the accepted domains (product, business, technical, strategy, culture)
- **identifier**: Descriptive slug or unique code

**Examples:**
- `unik-technical-jwt-authentication`
- `unik-business-pricing-strategy`
- `unik-product-user-onboarding`

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

### 🔹 `domain`
**Required** | **Enum**

Classification of the knowledge domain. **Accepted values:**

| Domain | Description | Examples |
|---------|-------------|----------|
| `product` | Product features, UX/UI, user flows | Interfaces, user journeys, features |
| `business` | Business rules, processes, strategies | Pricing, policies, business processes |
| `technical` | Code, architecture, infrastructure | APIs, databases, deployment |
| `strategy` | High-level decisions, planning | Roadmaps, strategic decisions |
| `culture` | Processes, methodology, team practices | Ceremonies, guidelines, values |

### 🔹 `type`
**Required** | **Enum**

Functional classification of content. **Accepted values:**

| Type | Description | Use |
|------|-------------|-----|
| `business_rule` | Business rule or constraint | Validation, decision logic |
| `function` | Reusable function or procedure | Code implementation |
| `template` | Reusable structure or pattern | Document creation, standardization |
| `guideline` | Guideline or best practice | Process orientation |
| `pattern` | Design or architectural pattern | Technical solutions |
| `decision` | Important decision record | Context and justification |
| `example` | Practical example or use case | Learning, demonstration |

### 🔹 `context`
**Required** | **Enum**

Development or usage context. **Accepted values:**

| Context | Description | When to use |
|---------|-------------|-------------|
| `discovery` | Research, analysis, requirements | Initial project phases |
| `implementation` | Development, construction | Active development |
| `refinement` | Improvement, optimization | Maintenance and evolution |
| `qa` | Quality, testing, validation | Quality assurance |
| `documentation` | Documentation, knowledge sharing | Documentation and training |
| `support` | Support, maintenance, operation | Post-production |

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
**Required for versions > 1.0.0** | **String**

Clear summary of changes implemented in the current version.

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
**Required for versions > 1.0.0** | **Enum**

Classification of the change impact for the current version.

**Accepted values:**
- `major`: Significant change affecting understanding or application
- `minor`: Compatible addition or improvement that maintains compatibility
- `patch`: Minor correction that doesn't alter meaning

### 🔹 `previous_version`
**Optional** | **String**

Reference to the immediately previous version for evolution traceability.

**Format:** `MAJOR.MINOR.PATCH`
**Usage:** Only required for versions > 1.0.0
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

### 🔹 `related_to`
**Optional** | **List of Strings**

List of IDs of other UKIs that are semantically related.

**Guidelines:**
- Use complete IDs (`unik-domain-identifier`)
- Create semantic networks
- Avoid excessive connections
- Prioritize direct relationships

**Examples:**
```yaml
related_to:
  - unik-technical-oauth-implementation
  - unik-business-user-authentication-policy
  - unik-product-login-flow
```

### 🔹 `last_validation`
**Optional** | **Date (YYYY-MM-DD)**

Date of last content review and validation.

**Purpose:**
- Quality control
- Content freshness
- Maintenance planning
- Trust indication

---

# 🎯 PRACTICAL USAGE EXAMPLES

## Example 1: Technical Pattern
```yaml
id: unik-technical-api-error-handling
title: Standardized API Error Handling Pattern
domain: technical
type: pattern
context: implementation
version: "1.2.0"
created_date: "2024-01-01"
last_modified: "2024-01-15"
change_summary: "Added timeout handling example and improved error code documentation"
change_impact: "minor"
previous_version: "1.1.0"
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
related_to:
  - unik-technical-api-response-format
  - unik-technical-logging-standards
last_validation: 2024-01-15
```

## Example 2: Business Rule
```yaml
id: unik-business-discount-calculation
title: Customer Discount Calculation Rule
domain: business
type: business_rule
context: implementation
version: "1.0.0"
created_date: "2024-01-10"
last_modified: "2024-01-10"
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
related_to:
  - unik-business-loyalty-program
  - unik-product-checkout-flow
last_validation: 2024-01-10
```

## Example 3: Product Guideline
```yaml
id: unik-product-modal-design
title: Modal Dialog Design Guidelines
domain: product
type: guideline
context: design
version: "2.1.0"
created_date: "2023-12-01"
last_modified: "2024-01-08"
change_summary: "Added accessibility requirements and mobile responsiveness guidelines"
change_impact: "minor"
previous_version: "2.0.0"
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
related_to:
  - unik-product-design-system
  - unik-technical-accessibility-standards
last_validation: 2024-01-08
```

---

# 🔄 SEMANTIC RELATIONSHIPS

## Types of Relationships

### 🔗 **Direct Dependencies**
UKIs that depend directly on each other for complete understanding.

**Example:**
```yaml
# unik-technical-jwt-implementation
related_to:
  - unik-technical-jwt-validation  # Direct dependency
```

### 🌐 **Contextual Associations**
UKIs that share context or work domain but are not directly dependent.

**Example:**
```yaml
# unik-product-user-onboarding
related_to:
  - unik-business-user-retention-strategy  # Same context
  - unik-technical-user-registration-api   # Same domain
```

### 📚 **Knowledge Hierarchies**
Parent-child relationships where one UKI is a specialization of another.

**Example:**
```yaml
# unik-technical-api-authentication (parent)
related_to:
  - unik-technical-jwt-authentication     # Specialization
  - unik-technical-oauth-authentication   # Specialization
```

## Relationship Guidelines

1. **Bidirectional**: If A relates to B, consider if B should relate to A
2. **Relevant**: Only include relationships that add real value
3. **Maintained**: Update relationships when UKIs are modified or removed
4. **Discoverable**: Relationships should help in knowledge navigation

---

# 🚀 IMPLEMENTATION GUIDELINES

## Organizing MEF Files

### Recommended File Structure
```
knowledge-base/
├── technical/
│   ├── unik-technical-api-patterns.yaml
│   └── unik-technical-database-schema.yaml
├── business/
│   ├── unik-business-pricing-rules.yaml
│   └── unik-business-customer-lifecycle.yaml
└── product/
    ├── unik-product-user-flows.yaml
    └── unik-product-design-system.yaml
```

### Implementation Considerations

Organizations implementing MEF should consider:

- **Validation**: Implement validation against MEF specification before storing UKIs
- **Indexing**: Extract structured metadata from UKI fields for search capabilities  
- **Versioning**: Track UKI evolution through the version control fields
- **Relationships**: Build semantic navigation through `related_to` connections
- **Domains**: Organize content by the five MEF domains for better discovery

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

---

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
