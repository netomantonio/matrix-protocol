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

id: unik:[domain]:[type]:[slug_or_id]
title: [Título objetivo e descritivo da unidade]
domain: [product | business | technical | strategy | culture]
type: [business_rule | function | template | guideline | pattern | decision | example]
context: [discovery | implementation | refinement | qa | documentation | support]
version: [MAJOR.MINOR.PATCH]  # Versionamento semântico da UKI
created_date: [YYYY-MM-DD]  # Data de criação da primeira versão
last_modified: [YYYY-MM-DD]  # Data da última modificação
change_summary: [Resumo das mudanças na versão atual]  # Opcional para versão inicial
change_impact: [major | minor | patch]  # Tipo de impacto da mudança
previous_version: [MAJOR.MINOR.PATCH]  # Versão anterior (opcional para versão inicial)

status: [active | deprecated | archived]  # OBRIGATÓRIO: controle de ciclo de vida

domain_of_influence: [strategy | finance | ethics | operations]  # RECOMENDADO: área de impacto

relationships:  # OBRIGATÓRIO: ontologia formal com tipos padronizados
  - type: [overrides | conflicts_with | complements | amends | depends_on]
    target: unik:[domain]:[type]:[identifier]
    description: [Descrição específica da relação ontológica]
  - type: [implements | extends | replaces | derives_from | relates_to]
    target: unik:[domain]:[type]:[identifier]
    description: [Descrição específica da relação semântica]

impact_analysis:  # OPCIONAL: análise de cadeia de impacto
  chain_preview:
    - unik:domain:type:item-a → unik:domain:type:item-b → unik:domain:type:item-c  # Cadeia de propagação prevista
  severity: [low | medium | high | critical]  # OBRIGATÓRIO: Severidade do impacto (padrão: medium se omitido)
  affected_domains: [lista de domínios afetados]
  propagation_estimate: [número estimado de UKIs impactadas]

sunset_policy: |  # OPCIONAL: política de revisão ou descontinuidade
  [Texto livre descrevendo condições de revisão, critérios de obsolescência,
   frequência de validação, ou condições para descontinuidade desta UKI]

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
governance:
  criticality: [critical | high | medium | low]  # Nível de criticidade para governança
  auto_propagation: [automatic | semi_automatic | manual]  # Modo de propagação automática
  validation_frequency: [30 | 60 | 90]  # Frequência de validação em dias
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

### 🔹 `id`
**Obrigatório** | **String** | **Único**

Identificador único seguindo o padrão `unik:[domain]:[type]:[identifier]`:
- **unik**: Prefixo fixo indicando uma Unidade de Conhecimento
- **domain**: Um dos domínios aceitos (product, business, technical, strategy, culture)
- **identifier**: Slug descritivo ou código único

**Exemplos:**
- `unik:technical:pattern:jwt-authentication`
- `unik:business:rule:pricing-strategy`
- `unik:product:guideline:user-onboarding`

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

| Tipo | Descrição | Uso | Categoria |
|------|-----------|-----|----------|
| `overrides` | Sobrescreve ou substitui outra UKI | Substituições diretas | Ontológica |
| `conflicts_with` | Conflita ou é incompatível | Incompatibilidades | Ontológica |
| `complements` | Complementa ou adiciona informação | Extensões colaborativas | Ontológica |
| `amends` | Modifica ou corrige parcialmente | Correções e ajustes | Ontológica |
| `depends_on` | Depende funcionalmente de outra UKI | Dependências estruturais | Ontológica |
| `implements` | Implementa um padrão ou especificação | Códigos que seguem padrões | Semântica |
| `extends` | Estende ou especializa um conceito | Heranças, refinamentos | Semântica |
| `replaces` | Substitui conhecimento anterior | Evoluções, migrações | Semântica |
| `derives_from` | Derivado ou baseado em outro conhecimento | Conhecimento originado | Semântica |
| `relates_to` | Relacionamento contextual genérico | Associações contextuais | Semântica |

**Formato Ontológico Padronizado:**
```yaml
relationships:
  - type: overrides
    target: unik:technical:pattern:legacy-auth
    description: Substitui método de autenticação legado por JWT
  - type: depends_on
    target: unik:technical:function:crypto-library
    description: Requer biblioteca de criptografia para validação de tokens
  - type: implements
    target: unik:technical:pattern:oauth-implementation
    description: Implementa padrão OAuth2 com PKCE para segurança
  - type: complements
    target: unik:technical:pattern:session-management
    description: Complementa gerenciamento de sessão com persistência
```

**Diretrizes de Uso:**
- Sempre usar formato `unik:[domain]:[type]:[identifier]` para referências
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
    - unik:technical:pattern:auth → unik:product:template:login → unik:technical:pattern:session
    - unik:technical:pattern:auth → unik:technical:guideline:api-security
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

### 🔹 `sunset_policy`
**Opcional** | **String (multilinha)**

Política de revisão, avaliação ou descontinuidade em texto livre.

**Exemplos de Uso:**
```yaml
sunset_policy: |
  Esta UKI deve ser revisada trimestralmente devido ao impacto em segurança.
  Considerar deprecação se novas tecnologias de autenticação forem adotadas.
  Critérios para arquivamento: substituição completa por OAuth3 ou similar.
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

### 🔹 `governance`
**Opcional** | **Objeto**

Configurações de governança ativa para controle automático de propagação e impacto.

**Estrutura:**
```yaml
governance:
  criticality: [critical | high | medium | low]
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
- **Conversão para unik-**
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
- Usar formato `unik:[domain]:[type]:[identifier]` para referências
- **Escolher tipos precisos**: ontológicos para relações estruturais, semânticos para conceituais
- **EVITAR** relacionamento `relates_to` - preferir tipos específicos
- **VALIDAR** que target existe antes de criar relacionamento
- **DOCUMENTAR** claramente a natureza específica de cada relação

### 🌍 **Campo `domain_of_influence` (Recomendado)**
- Usar para UKIs com impacto organizacional significativo
- `strategy`: para decisões de alto nível e direcionamento
- `finance`: para regras que impactam custos, preços ou receita
- `ethics`: para questões de compliance, privacidade ou conduta
- `operations`: para processos operacionais e eficiência

### 📊 **Campo `impact_analysis` (Opcional)**
- **MAPEAR** cadeias de propagação previstas antes de mudanças MAJOR
- Estimar número realista de UKIs impactadas
- Usar severity `critical` apenas para UKIs que quebram funcionalidade básica
- **ATUALIZAR** quando relacionamentos mudarem significativamente

### 📅 **Campo `sunset_policy` (Opcional)**
- **DEFINIR** para UKIs críticas ou que dependem de tecnologias externas
- Incluir critérios objetivos para revisão e descontinuidade
- **MENCIONAR** marcos tecnológicos ou organizacionais relevantes
- Ser específico sobre frequência de revisão (trimestral, semestral, anual)

## ⚠️ Diretrizes de Coerência Semântica

- **EVITAR** duplicação de informações entre campos `relationships` e outros campos
- **MANTER** consistência ontológica: se A `overrides` B, então B deve estar `deprecated`
- **VALIDAR** que UKIs com status `deprecated` não sejam target de novos relacionamentos `implements`
- **VERIFICAR** que `domain_of_influence` seja coerente com `domain` e `type`
- **GARANTIR** que `impact_analysis.severity` seja proporcional ao número de relacionamentos

## 🔄 Governança de Mudanças

- **ANALISAR** impacto em UKIs relacionadas antes de mudanças MAJOR
- **PROPAGAR** mudanças seguindo a ontologia de relacionamentos
- **NOTIFICAR** stakeholders baseado em `domain_of_influence`
- **REAVALIAR** `sunset_policy` quando contexto organizacional mudar
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
id: unik:technical:pattern:api-error-handling
title: Padrão de Tratamento de Erros em API
domain: technical
type: pattern
context: implementation
version: "1.0.0"
created_date: "2024-01-15"
last_modified: "2024-01-15"

status: active
domain_of_influence: operations

relationships:
  - type: implements
    target: unik:technical:template:api-response-format
    description: Implementa formato padrão de resposta da API com estrutura de erro
  - type: complements
    target: unik:technical:guideline:logging-standards
    description: Complementa padrões de logging para auditoria e debugging
  - type: depends_on
    target: unik:[domain]:[type]:[identifier]
    description: Depende de definições padronizadas de códigos HTTP

impact_analysis:
  chain_preview:
    - unik:[domain]:[type]:[identifier] → unik:[domain]:[type]:[identifier]
    - unik:[domain]:[type]:[identifier] → unik:[domain]:[type]:[identifier]
  severity: medium
  affected_domains: [technical, product]
  propagation_estimate: 8

sunset_policy: |
  Revisar anualmente ou quando novos padrões de API forem adotados.
  Considerar deprecação se GraphQL ou outras tecnologias substituirem REST.
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
id: unik:business:rule:discount-calculation
title: Regra de Cálculo de Desconto de Cliente
domain: business
type: business_rule
context: implementation
version: "1.2.0"
created_date: "2024-01-10"
last_modified: "2024-01-15"
change_summary: "Adicionado desconto para clientes premium e limite máximo"
change_impact: "minor"
previous_version: "1.1.0"

status: active
domain_of_influence: finance

relationships:
  - type: implements
    target: unik:[domain]:[type]:[identifier]
    description: Implementa regras do programa de fidelidade para cálculo automático
  - type: complements
    target: unik:[domain]:[type]:[identifier]
    description: Complementa processo de checkout com lógica de preço final
  - type: depends_on
    target: unik:[domain]:[type]:[identifier]
    description: Depende de classificação de perfil de cliente para funcionar
  - type: overrides
    target: unik:[domain]:[type]:[identifier]
    description: Substitui regras de desconto manuais anteriores

impact_analysis:
  chain_preview:
    - unik:[domain]:[type]:[identifier] → unik:[domain]:[type]:[identifier] → unik:[domain]:[type]:[identifier]
    - unik:[domain]:[type]:[identifier] → unik:[domain]:[type]:[identifier]
  severity: high
  affected_domains: [business, finance, product]
  propagation_estimate: 15

sunset_policy: |
  Revisar trimestralmente devido ao impacto financeiro direto.
  Reavaliar se novos modelos de fidelidade forem implementados.
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
  ```
  desconto_base = perfil_cliente.desconto_percentual
  desconto_premium = cliente.is_premium ? 5 : 0
  desconto_total = min(desconto_base + desconto_premium, 25)
  valor_final = valor_original * (1 - desconto_total/100)
  ```
examples:
  - input: "Cliente fiel premium comprando R$ 1000"
    output: "Desconto 20% (15% + 5%), valor final R$ 800"
  - input: "Cliente novo comprando R$ 500"
    output: "Desconto 5%, valor final R$ 475"
last_validation: "2024-01-15"
```

## Exemplo 3: Diretriz de Produto
```yaml
id: unik:product:guideline:modal-design
title: Diretrizes de Design para Modais
domain: product
type: guideline
context: design
version: "1.0.0"
created_date: "2024-01-08"
last_modified: "2024-01-08"

status: active
domain_of_influence: operations

relationships:
  - type: implements
    target: unik:[domain]:[type]:[identifier]
    description: Implementa componentes padronizados do sistema de design
  - type: depends_on
    target: unik:[domain]:[type]:[identifier]
    description: Depende de padrões de acessibilidade para compliance
  - type: complements
    target: unik:[domain]:[type]:[identifier]
    description: Complementa biblioteca de componentes com especificações de modal

impact_analysis:
  chain_preview:
    - unik:[domain]:[type]:[identifier] → unik:[domain]:[type]:[identifier] → unik:[domain]:[type]:[identifier]
    - unik:[domain]:[type]:[identifier] → unik:[domain]:[type]:[identifier]
  severity: medium
  affected_domains: [product, technical]
  propagation_estimate: 6

sunset_policy: |
  Revisar semestralmente com time de design e acessibilidade.
  Reavaliar quando novos frameworks de UI forem adotados.
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

### 🏗️ **Dependências de Implementação** (`implements` / `depends_on`)
UKIs que implementam padrões ou dependem de outros conhecimentos para funcionalidade.

**Exemplos:**
```yaml
# unik:technical:function:jwt-implementation
relationships:
  - target: unik:technical:function:jwt-validation
    type: depends_on
    description: Requer lógica de validação JWT para funcionar adequadamente
  - target: unik:technical:pattern:authentication
    type: implements
    description: Implementa o padrão de autenticação padronizado
```

### 🌿 **Evolução do Conhecimento** (`extends` / `derives_from` / `replaces`)
UKIs que representam evolução, especialização ou substituição de conhecimento.

**Exemplos:**
```yaml
# unik:technical:function:oauth2-implementation
relationships:
  - target: unik:technical:pattern:oauth-basic
    type: extends
    description: Estende OAuth básico com PKCE e refresh tokens
  - target: unik:technical:pattern:legacy-auth
    type: replaces
    description: Substitui método de autenticação descontinuado
```

### 🛡️ **Relacionamentos de Conformidade** (`complies_with` / `conflicts_with`)
UKIs que seguem políticas ou identificam incompatibilidades.

**Exemplos:**
```yaml
# unik:technical:guideline:encryption-standard
relationships:
  - target: unik:business:policy:data-protection
    type: complies_with
    description: Segue requisitos de proteção de dados corporativos
  - target: unik:technical:pattern:legacy-encryption
    type: conflicts_with
    description: Incompatível com métodos de criptografia descontinuados
```

### 🌐 **Associações Contextuais** (`relates_to`)
Relacionamentos genéricos para conexões contextuais que não se encaixam em tipos específicos.

**Exemplo:**
```yaml
# unik:product:guideline:user-onboarding
relationships:
  - target: unik:technical:function:user-registration-api
    type: relates_to
    description: Compartilha contexto no domínio de gestão de usuários
  - target: unik:business:rule:user-retention-strategy
    type: relates_to
    description: Contribui para estratégia de retenção de usuários
```

## Diretrizes de Relacionamento

1. **Precisão Semântica**: Use tipos específicos de relação quando aplicável
2. **Consistência Bidirecional**: Garanta que relacionamentos reversos façam sentido semântico
3. **Descrições Claras**: Sempre forneça descrições significativas para cada relacionamento
4. **Governança Habilitada**: Relacionamentos tipados permitem análise de impacto e validação automatizada

# 🎛️ GOVERNANÇA ATIVA E PROPAGAÇÃO AUTOMÁTICA

O MEF implementa um sistema de **governança ativa** que utiliza relacionamentos semânticos tipados para propagar automaticamente mudanças e manter consistência em redes de conhecimento interconectadas.

## 🔄 Regras de Propagação por Tipo de Relacionamento

### 📋 **`implements`** - Propagação de Padrões
**Regra:** Mudanças em padrões/diretrizes devem ser propagadas para suas implementações.

**Comportamento:**
- **MAJOR**: Notificar implementações sobre incompatibilidade
- **MINOR**: Sugerir adoção de melhorias opcionais
- **PATCH**: Informar correções aplicáveis

**Algoritmo:**
```yaml
when: change in base-UKI (pattern/guideline)
propagation:
  to: UKIs where { type: implements, target: base-UKI }
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

### 🌿 **`extends`** - Extensões
**Regra:** Mudanças em conceitos base devem ser avaliadas para extensões.

**Comportamento:**
- **MAJOR**: Avaliar se extensão ainda é válida
- **MINOR**: Considerar incorporação de melhorias
- **PATCH**: Verificar relevância da correção

**Algoritmo:**
```yaml
when: change in base-UKI
propagation:
  to: UKIs where { type: extends, target: base-UKI }
  action:
    - major: mark as "extension_requires_review"
    - minor: mark as "consider_incorporation"
    - patch: mark as "assess_relevance"
```

### 🔄 **`replaces`** - Deprecação Automática
**Regra:** Mudanças em substitutos devem atualizar status de substituídos.

**Comportamento:**
- **MAJOR**: Marcar substituído como descontinuado
- **MINOR**: Atualizar recomendação de migração
- **PATCH**: Informar sobre melhorias do substituto

**Algoritmo:**
```yaml
when: change in replacement-UKI
propagation:
  to: UKIs where { type: replaces, source: replacement-UKI }
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
    - unik:technical:pattern:change → unik:product:guideline:ui-patterns → unik:business:rule:validation
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
| MAJOR | implements | CRÍTICA | Revisão obrigatória |
| MAJOR | depends_on | CRÍTICA | Validação compatibilidade |
| MAJOR | extends | ALTA | Revisão extensão |
| MINOR | implements | MÉDIA | Considerar adoção |
| MINOR | depends_on | MÉDIA | Validar funcionamento |
| PATCH | qualquer | BAIXA | Informar disponibilidade |

### 🔄 Algoritmo de Cascata de Versionamento

```yaml
cascade_versioning:
  trigger: "change in source-UKI"
  process:
    1. identify_related:
        query: "SELECT * FROM ukis WHERE relationships.target = source-UKI"
    2. classify_impact:
        for_each: relationship
        calculate: impact_by_type[relationship.type]
    3. generate_proposals:
        for_each: related-UKI
        propose: new_version_based_on_impact
    4. execute_propagation:
        order: priority (critical → high → medium → low)
        mode: automatic | semi-automatic | manual
```

## 🚨 Detecção de Conflitos e Inconsistências

### 🔍 Validações Automáticas

```yaml
validations:
  semantic_consistency:
    - "UKI que implements deve ser compatível com target"
    - "UKI que replaces deve ter domain similar ao target"
    - "UKI que extends deve manter compatibilidade base"
  
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
| `product` | Design de produto, experiência do usuário e especificações de interface | Diretrizes de interface, padrões de design, padrões de acessibilidade, definições de jornada do usuário |
| `business` | Regras de negócio, processos e conhecimento operacional | Cálculos de preços, regras de desconto, definições de workflow, especificações de lógica de negócio |
| `technical` | Implementações técnicas, arquitetura e padrões de código | Padrões de autenticação, especificações de API, schemas de banco de dados, templates de código |
| `strategy` | Decisões estratégicas, roadmaps e planejamento de longo prazo | Estratégias de evolução de API, planos de migração de tecnologia, decisões de arquitetura, prioridades de investimento |
| `culture` | Cultura de equipe, processos de colaboração e conhecimento organizacional | Processos de code review, diretrizes de comunicação da equipe, procedimentos de onboarding, padrões de qualidade |

### Tipos (`type`)

| Tipo | Descrição | Domínios Aplicáveis |
|------|-----------|---------------------|
| `business_rule` | Lógica de negócio formal e regras operacionais | business, product, strategy |
| `function` | Funções executáveis, algoritmos e procedimentos computacionais | technical, business |
| `template` | Templates reutilizáveis e formatos padronizados | technical, product, culture |
| `guideline` | Melhores práticas e abordagens recomendadas | product, technical, culture, strategy |
| `pattern` | Soluções recorrentes e padrões de design | technical, product, business |
| `decision` | Decisões estratégicas e escolhas arquiteturais | strategy, technical, business |
| `example` | Exemplos concretos e amostras de implementação | technical, product, business, culture, strategy |

### Níveis de Severidade (`severity`)

| Nível | Descrição | Impacto |
|-------|-----------|---------|
| `low` | Impacto menor, informacional ou sugestões de melhoria | Impacto mínimo nos negócios ou técnico |
| `medium` | Impacto moderado, afeta funcionalidades ou processos específicos | Impacto localizado na funcionalidade ou experiência do usuário |
| `high` | Impacto significativo, afeta funcionalidades centrais ou operações de negócio | Impacto substancial na funcionalidade do sistema ou processos de negócio |
| `critical` | Impacto crítico, falha do sistema ou grande disrupção de negócio | Impacto severo causando falha do sistema ou grande disrupção de negócio |

### Tipos de Relacionamento (`relationships.type`)

#### Ontológicos
| Tipo | Descrição | Direcionalidade |
|------|-----------|-----------------|
| `implements` | UKI alvo fornece implementação concreta de conceito abstrato | unidirecional |
| `depends_on` | UKI origem requer UKI alvo para funcionamento adequado | unidirecional |
| `extends` | UKI origem constrói sobre e expande UKI alvo | unidirecional |
| `replaces` | UKI origem substitui e supera UKI alvo | unidirecional |
| `complies_with` | UKI origem adere aos padrões definidos no UKI alvo | unidirecional |
| `conflicts_with` | UKI origem contradiz ou é incompatível com UKI alvo | bidirecional |

#### Semânticos
| Tipo | Descrição | Direcionalidade |
|------|-----------|-----------------|
| `derives_from` | UKI origem origina-se de ou é baseado no UKI alvo | unidirecional |
| `relates_to` | Relacionamento semântico geral sem hierarquia específica | bidirecional |

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

---

# 🔧 STANDARD STRUCTURE OF A UKI

## 📌 Format: **Structured YAML**

Each file represents a **single UKI**.

```yaml

id: unik:[domain]:[type]:[slug_or_id]
title: [Objective and descriptive title of the unit]
domain: [product | business | technical | strategy | culture]
type: [business_rule | function | template | guideline | pattern | decision | example]
context: [discovery | implementation | refinement | qa | documentation | support]
version: [MAJOR.MINOR.PATCH]  # Semantic versioning of the UKI
created_date: [YYYY-MM-DD]  # Date of first version creation
last_modified: [YYYY-MM-DD]  # Date of last modification
change_summary: [Summary of changes in current version]  # Optional for initial version
change_impact: [major | minor | patch]  # Type of change impact
previous_version: [MAJOR.MINOR.PATCH]  # Previous version (optional for 1.0.0)

status: [active | deprecated | archived]  # Lifecycle control
domain_of_influence: [strategy | finance | ethics | operations]  # Strategic impact area

relationships:  # Formal ontology of typed relationships
  - type: [overrides | conflicts_with | complements | amends | depends_on]
    target: unik:[domain]:[type]:[identifier]
    description: [Specific description of the ontological relationship]
  - type: [implements | extends | replaces | derives_from | relates_to]
    target: unik:[domain]:[type]:[identifier]
    description: [Specific description of the semantic relationship]

impact_analysis:  # Impact chain analysis
  chain_preview:
    - unik:domain:type:item-a → unik:domain:type:item-b → unik:domain:type:item-c  # Expected propagation chain
  severity: [low | medium | high | critical]  # REQUIRED: Impact severity (default: medium if omitted)
  affected_domains: [list of affected domains]
  propagation_estimate: [estimated number of impacted UKIs]

sunset_policy: |
  [Review policy, obsolescence criteria and discontinuation conditions]
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
governance:
  criticality: [critical | high | medium | low]  # Criticality level for governance
  auto_propagation: [automatic | semi_automatic | manual]  # Automatic propagation mode
  validation_frequency: [30 | 60 | 90]  # Validation frequency in days
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

### 🔹 `id`
**Required** | **String** | **Unique**

Unique identifier following the pattern `unik:[domain]:[type]:[identifier]`:
- **unik**: Fixed prefix indicating it's a Knowledge Unit
- **domain**: One of the accepted domains (product, business, technical, strategy, culture)
- **identifier**: Descriptive slug or unique code

**Examples:**
- `unik:technical:pattern:jwt-authentication`
- `unik:business:rule:pricing-strategy`
- `unik:product:guideline:user-onboarding`

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

| Type | Description | Usage | Category |
|------|-------------|-------|----------|
| `overrides` | Overrides or replaces another UKI | Direct replacements | Ontological |
| `conflicts_with` | Conflicts or is incompatible | Incompatibilities | Ontological |
| `complements` | Complements or adds information | Collaborative extensions | Ontological |
| `amends` | Modifies or partially corrects | Corrections and adjustments | Ontological |
| `depends_on` | Functionally depends on another UKI | Structural dependencies | Ontological |
| `implements` | Implements a pattern or specification | Code following patterns | Semantic |
| `extends` | Extends or specializes a concept | Inheritance, refinements | Semantic |
| `replaces` | Replaces previous knowledge | Evolutions, migrations | Semantic |
| `derives_from` | Derived or based on other knowledge | Originated knowledge | Semantic |
| `relates_to` | Generic contextual relationship | Contextual associations | Semantic |

**Standardized Ontological Format:**
```yaml
relationships:
  - type: overrides
    target: unik:technical:pattern:legacy-auth
    description: Replaces legacy authentication method with JWT
  - type: depends_on
    target: unik:technical:function:crypto-library
    description: Requires cryptography library for token validation
  - type: implements
    target: unik:technical:pattern:oauth-implementation
    description: Implements OAuth2 pattern with PKCE for security
  - type: complements
    target: unik:technical:pattern:session-management
    description: Complements session management with persistence
```

**Usage Guidelines:**
- Always use `unik:[domain]:[type]:[identifier]` format for references
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
    - unik:technical:pattern:auth → unik:product:template:login → unik:technical:pattern:session
    - unik:technical:pattern:auth → unik:technical:guideline:api-security
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

### 🔹 `sunset_policy`
**Optional** | **String (multiline)**

Review, assessment or discontinuation policy in free text.

**Usage Examples:**
```yaml
sunset_policy: |
  This UKI should be reviewed quarterly due to security impact.
  Consider deprecation if new authentication technologies are adopted.
  Archival criteria: complete replacement by OAuth3 or similar.
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
governance:
  criticality: [critical | high | medium | low]
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
id: unik:technical:pattern:api-error-handling
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

status: active
domain_of_influence: operations

relationships:
  - type: implements
    target: unik:technical:template:api-response-format
    description: Implements standard API response format with error structure
  - type: complements
    target: unik:technical:guideline:logging-standards
    description: Complements logging standards for auditing and debugging
  - type: depends_on
    target: unik:[domain]:[type]:[identifier]
    description: Depends on standardized HTTP status code definitions

impact_analysis:
  chain_preview:
    - unik:[domain]:[type]:[identifier] → unik:[domain]:[type]:[identifier]
    - unik:[domain]:[type]:[identifier] → unik:[domain]:[type]:[identifier]
  severity: medium
  affected_domains: [technical, product]
  propagation_estimate: 8

sunset_policy: |
  Review annually or when new API standards are adopted.
  Consider deprecation if GraphQL or other technologies replace REST.
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
id: unik:business:rule:discount-calculation
title: Customer Discount Calculation Rule
domain: business
type: business_rule
context: implementation
version: "1.0.0"
created_date: "2024-01-10"
last_modified: "2024-01-10"

status: active
domain_of_influence: finance

relationships:
  - type: implements
    target: unik:[domain]:[type]:[identifier]
    description: Implements loyalty program rules for automatic calculation
  - type: complements
    target: unik:[domain]:[type]:[identifier]
    description: Complements checkout process with final pricing logic
  - type: depends_on
    target: unik:[domain]:[type]:[identifier]
    description: Depends on customer profile classification to function

impact_analysis:
  chain_preview:
    - unik:[domain]:[type]:[identifier] → unik:[domain]:[type]:[identifier] → unik:[domain]:[type]:[identifier]
    - unik:[domain]:[type]:[identifier] → unik:[domain]:[type]:[identifier]
  severity: high
  affected_domains: [business, finance, product]
  propagation_estimate: 12

sunset_policy: |
  Review quarterly due to direct financial impact.
  Reevaluate if new loyalty models are implemented.
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
id: unik:product:guideline:modal-design
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

status: active
domain_of_influence: operations

relationships:
  - type: implements
    target: unik:[domain]:[type]:[identifier]
    description: Implements standardized design system components
  - type: depends_on
    target: unik:[domain]:[type]:[identifier]
    description: Depends on accessibility standards for compliance
  - type: complements
    target: unik:[domain]:[type]:[identifier]
    description: Complements component library with modal specifications

impact_analysis:
  chain_preview:
    - unik:[domain]:[type]:[identifier] → unik:[domain]:[type]:[identifier] → unik:[domain]:[type]:[identifier]
    - unik:[domain]:[type]:[identifier] → unik:[domain]:[type]:[identifier]
  severity: medium
  affected_domains: [product, technical]
  propagation_estimate: 6

sunset_policy: |
  Review semi-annually with design and accessibility teams.
  Reevaluate when new UI frameworks are adopted.
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

### 🏗️ **Implementation Dependencies** (`implements` / `depends_on`)
UKIs that implement patterns or depend on other knowledge for functionality.

**Examples:**
```yaml
# unik:technical:function:jwt-implementation
relationships:
  - target: unik:technical:function:jwt-validation
    type: depends_on
    description: Requires JWT validation logic to function properly
  - target: unik:technical:pattern:authentication
    type: implements
    description: Implements the standardized authentication pattern
```

### 🌿 **Knowledge Evolution** (`extends` / `derives_from` / `replaces`)
UKIs that represent knowledge evolution, specialization or replacement.

**Examples:**
```yaml
# unik:technical:function:oauth2-implementation
relationships:
  - target: unik:technical:pattern:oauth-basic
    type: extends
    description: Extends basic OAuth with PKCE and refresh tokens
  - target: unik:technical:pattern:legacy-auth
    type: replaces
    description: Replaces deprecated authentication method
```

### 🛡️ **Compliance Relationships** (`complies_with` / `conflicts_with`)
UKIs that follow policies or identify incompatibilities.

**Examples:**
```yaml
# unik:technical:guideline:encryption-standard
relationships:
  - target: unik:business:policy:data-protection
    type: complies_with
    description: Follows corporate data protection requirements
  - target: unik:technical:pattern:legacy-encryption
    type: conflicts_with
    description: Incompatible with deprecated encryption methods
```

### 🌐 **Contextual Associations** (`relates_to`)
Generic relationships for contextual connections that don't fit specific types.

**Example:**
```yaml
# unik:product:guideline:user-onboarding
relationships:
  - target: unik:technical:function:user-registration-api
    type: relates_to
    description: Shares context in user management domain
  - target: unik:business:rule:user-retention-strategy
    type: relates_to
    description: Contributes to user retention strategy
```

## Relationship Guidelines

1. **Semantic Precision**: Use specific relation types when applicable
2. **Bidirectional Consistency**: Ensure reverse relationships make semantic sense
3. **Clear Descriptions**: Always provide meaningful descriptions for each relationship
4. **Governance Enabled**: Typed relationships enable automated impact analysis and validation

# 🎛️ ACTIVE GOVERNANCE AND AUTOMATIC PROPAGATION

MEF implements an **active governance** system that uses typed semantic relationships to automatically propagate changes and maintain consistency in interconnected knowledge networks.

## 🔄 Propagation Rules by Relationship Type

### 📋 **`implements`** - Pattern Propagation
**Rule:** Changes in patterns/guidelines should be propagated to their implementations.

**Behavior:**
- **MAJOR**: Notify implementations about incompatibility
- **MINOR**: Suggest adoption of optional improvements
- **PATCH**: Inform applicable corrections

**Algorithm:**
```yaml
when: change in base-UKI (pattern/guideline)
propagation:
  to: UKIs where { type: implements, target: base-UKI }
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

### 🌿 **`extends`** - Extension Updates
**Rule:** Changes in base concepts should be evaluated for extensions.

**Behavior:**
- **MAJOR**: Evaluate if extension is still valid
- **MINOR**: Consider incorporating improvements
- **PATCH**: Check relevance of correction

**Algorithm:**
```yaml
when: change in base-UKI
propagation:
  to: UKIs where { type: extends, target: base-UKI }
  action:
    - major: mark as "extension_requires_review"
    - minor: mark as "consider_incorporation"
    - patch: mark as "assess_relevance"
```

### 🔄 **`replaces`** - Automatic Deprecation
**Rule:** Changes in replacements should update status of replaced items.

**Behavior:**
- **MAJOR**: Mark replaced as discontinued
- **MINOR**: Update migration recommendation
- **PATCH**: Inform about replacement improvements

**Algorithm:**
```yaml
when: change in replacement-UKI
propagation:
  to: UKIs where { type: replaces, source: replacement-UKI }
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
    - unik:technical:pattern:change → unik:product:guideline:ui-patterns → unik:business:rule:validation
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
| MAJOR | implements | CRITICAL | Mandatory review |
| MAJOR | depends_on | CRITICAL | Compatibility validation |
| MAJOR | extends | HIGH | Extension review |
| MINOR | implements | MEDIUM | Consider adoption |
| MINOR | depends_on | MEDIUM | Validate functionality |
| PATCH | any | LOW | Inform availability |

### 🔄 Cascade Versioning Algorithm

```yaml
cascade_versioning:
  trigger: "change in source-UKI"
  process:
    1. identify_related:
        query: "SELECT * FROM ukis WHERE relationships.target = source-UKI"
    2. classify_impact:
        for_each: relationship
        calculate: impact_by_type[relationship.type]
    3. generate_proposals:
        for_each: related-UKI
        propose: new_version_based_on_impact
    4. execute_propagation:
        order: priority (critical → high → medium → low)
        mode: automatic | semi-automatic | manual
```

## 🚨 Conflict and Inconsistency Detection

### 🔍 Automatic Validations

```yaml
validations:
  semantic_consistency:
    - "UKI that implements must be compatible with target"
    - "UKI that replaces must have similar domain to target"
    - "UKI that extends must maintain base compatibility"
  
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
│   ├── unik-technical-pattern-api.yaml
│   └── unik-technical-template-database-schema.yaml
├── business/
│   ├── unik-business-rule-pricing-rules.yaml
│   └── unik-business-rule-customer-lifecycle.yaml
└── product/
    ├── unik-product-template-user-flows.yaml
    └── unik-product-guideline-design-system.yaml
```

### Implementation Considerations

Organizations implementing MEF should consider:

- **Validation**: Implement validation against MEF specification before storing UKIs
- **Indexing**: Extract structured metadata from UKI fields for search capabilities  
- **Versioning**: Track UKI evolution through the version control fields
- **Relationships**: Build semantic navigation through `relationships` connections
- **Domains**: Organize content by the five MEF domains for better discovery

# 📚 AUXILIARY ONTOLOGY

## Controlled Vocabulary for MEF Fields

This section defines the accepted controlled vocabulary for `domain`, `type`, `severity`, `relationship.type`, `maturity_level`, and `provenance.source_type` fields to ensure semantic consistency across UKI implementations.

### Domains (`domain`)

| Domain | Description | Examples |
|--------|-------------|----------|
| `product` | Product design, user experience, and interface specifications | User interface guidelines, design patterns, accessibility standards, user journey definitions |
| `business` | Business rules, processes, and operational knowledge | Pricing calculations, discount rules, workflow definitions, business logic specifications |
| `technical` | Technical implementations, architecture, and code patterns | Authentication patterns, API specifications, database schemas, code templates |
| `strategy` | Strategic decisions, roadmaps, and long-term planning | API evolution strategies, technology migration plans, architecture decisions, investment priorities |
| `culture` | Team culture, collaboration processes, and organizational knowledge | Code review processes, team communication guidelines, onboarding procedures, quality standards |

### Types (`type`)

| Type | Description | Applicable Domains |
|------|-------------|-------------------|
| `business_rule` | Formal business logic and operational rules | business, product, strategy |
| `function` | Executable functions, algorithms, and computational procedures | technical, business |
| `template` | Reusable templates and standardized formats | technical, product, culture |
| `guideline` | Best practices and recommended approaches | product, technical, culture, strategy |
| `pattern` | Recurring solutions and design patterns | technical, product, business |
| `decision` | Strategic decisions and architectural choices | strategy, technical, business |
| `example` | Concrete examples and implementation samples | technical, product, business, culture, strategy |

### Severity Levels (`severity`)

| Level | Description | Impact |
|-------|-------------|--------|
| `low` | Minor impact, informational or enhancement suggestions | Minimal business or technical impact |
| `medium` | Moderate impact, affects specific functionality or processes | Localized impact on functionality or user experience |
| `high` | Significant impact, affects core functionality or business operations | Substantial impact on system functionality or business processes |
| `critical` | Critical impact, system failure or major business disruption | Severe impact causing system failure or major business disruption |

### Relationship Types (`relationships.type`)

#### Ontological
| Type | Description | Directionality |
|------|-------------|----------------|
| `implements` | Target UKI provides concrete implementation of abstract concept | unidirectional |
| `depends_on` | Source UKI requires target UKI for proper functioning | unidirectional |
| `extends` | Source UKI builds upon and expands target UKI | unidirectional |
| `replaces` | Source UKI supersedes and substitutes target UKI | unidirectional |
| `complies_with` | Source UKI adheres to standards defined in target UKI | unidirectional |
| `conflicts_with` | Source UKI contradicts or is incompatible with target UKI | bidirectional |

#### Semantic
| Type | Description | Directionality |
|------|-------------|----------------|
| `derives_from` | Source UKI originates from or is based on target UKI | unidirectional |
| `relates_to` | General semantic relationship without specific hierarchy | bidirectional |

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

### Influence Domains (`domain_of_influence`)

| Domain | Description | Impact |
|--------|-------------|--------|
| `strategy` | Strategic decisions and organizational direction | Affects long-term objectives, investments, and organizational priorities |
| `finance` | Financial and budgetary aspects | Impacts costs, revenue, ROI, and investment decisions |
| `ethics` | Ethical considerations and compliance | Influences conduct policies, regulatory compliance, and social responsibility |
| `operations` | Daily operations and processes | Affects operational efficiency, workflows, and task execution |

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
