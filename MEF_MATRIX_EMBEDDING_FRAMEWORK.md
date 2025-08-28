# MEF — Matrix Embedding Framework
**Acronym:** MEF  
**Status:** Stable  
**Version:** 1.0.0  
**Date:** 2025-01-25  

---

## 1. Introduction

The **Matrix Embedding Framework (MEF)** specifies in a comprehensive, standardized, and internationalized way the minimum and complete structure of versioned embedded knowledge to be used by people and intelligent agents in the context of the Matrix Protocol.

MEF defines a **standardized model for versioned knowledge structuring** that allows any member of a multidisciplinary team to create, register, interlink, and use minimal knowledge units — called **UKIs (Units of Knowledge Interlinked)**.

These units are embedded and consumed by intelligent agents, ensuring traceability, applicability, controlled evolution, and real-time contextual intelligence.

---

## 2. Terms and Definitions

- **UKI**: Units of Knowledge Interlinked - basic units of structured knowledge
- **Semantic Versioning**: Version control following MAJOR.MINOR.PATCH standard
- **Ontological Relationships**: Typed connections between UKIs (depends_on, overrides, etc.)
- **Knowledge Promotion**: Formal process of elevating scope or maturity
- ***_ref Fields**: Fields that reference nodes defined in the organizational MOC
- **Scope Mode**: Propagation behavior (restricted vs propagated)
- **Maturity Reference**: Epistemological validation level from organizational MOC

Cross-reference to **MOC (Matrix Ontology Catalog)** for organizational taxonomy definitions.

---

## 3. Core Concepts

### UKI Structure Foundation
Each UKI is a structured YAML file containing:
- **Mandatory metadata**: id, title, version, dates
- **MOC references**: scope_ref, domain_ref, type_ref, maturity_ref
- **Content**: Specific structured knowledge
- **Relationships**: Typed connections to other UKIs
- **Lifecycle control**: Status and lifecycle management

### MOC Integration
MEF uses **MOC as the single source of organizational taxonomies**:
- ***_ref Fields**: All hierarchical fields reference nodes defined in organizational MOC
- **Local Flexibility**: Organizations configure their own hierarchies while maintaining universal MEF structure
- **Integrated Governance**: MOC defines authority and visibility rules that MEF respects during UKI creation and consultation

### MEP Epistemological Guidance
MEF implements epistemological principles established by **Matrix Epistemic Principle (MEP)**:
- **Stratification**: maturity_ref field reflects epistemological levels (draft → validated → approved)
- **Responsible Promotion**: promotion_rationale field documents justifications for knowledge evolution
- **Derived Authority**: scope_ref and governance_ref fields implement contextual and relative authority

---

## 4. Normative Rules

> ⚠️ This section is **normative**.

### Mandatory UKI Structure
Every UKI MUST contain:
- **id**: Unique identifier in format uki:[domain_ref]:[type_ref]:[slug]
- **title**: Descriptive and objective title
- **version**: Semantic versioning MAJOR.MINOR.PATCH
- **scope_ref, domain_ref, type_ref**: Valid references to organizational MOC
- **created_date, last_modified**: Creation and modification dates
- **status**: Lifecycle state (active, deprecated, archived)

### Mandatory Versioning Rules
- MUST follow semantic MAJOR.MINOR.PATCH standard
- MUST include change_summary for versions after initial
- MUST reference previous_version when applicable
- MUST classify change_impact (major, minor, patch)

### Mandatory Relationship Rules
- MUST use standardized types: depends_on, overrides, conflicts_with, complements, amends, precedes, equivalent_to
- MUST include specific description for each relationship
- MUST reference valid UKIs in correct format

### MOC Integration Requirements
- All *_ref fields MUST reference valid MOC nodes
- scope_mode MUST be either "restricted" or "propagated"
- maturity_ref MUST follow organizational MOC maturity hierarchy
- Implementations MUST validate MOC references before UKI creation

### Decision Record Persistence (MAL Integration)
- MEF implementations MUST persist MAL Decision Records as immutable audit trail
- Decision Records MUST be stored with complete arbitration metadata
- UKIs resulting from MAL arbitration MUST reference the corresponding Decision Record
- Decision Record relationships (conflicts_with, supersedes, partitioned_by_scope) MUST be maintained
- Decision Records MUST NOT be modifiable after creation

---

## 5. Interoperability

MEF integrates with all Matrix Protocol frameworks through structured knowledge exchange and validation:

- **MOC (Matrix Ontology Catalog)**: Defines organizational taxonomies referenced by *_ref fields; validates UKI hierarchical references; provides governance rules for knowledge creation and promotion
- **MEP (Matrix Epistemic Principle)**: Provides epistemological foundations for versioning and promotion; guides responsible promotion through promotion_rationale requirements; implements stratified epistemology via maturity_ref
- **ZOF (Zion Orchestration Framework)**: Consumes UKIs during Understand state Oracle consultation; produces new UKIs during Enrich state; validates enrichment through EvaluateForEnrich checkpoint; invokes MAL for conflict resolution
- **OIF (Operator Intelligence Framework)**: Uses UKIs to feed Knowledge Agent semantic search and relationship mapping; processes UKI metadata for contextual filtering and explanation generation; accesses Decision Record data for arbitration explanations
- **MAL (Matrix Arbiter Layer)**: Relies on MEF to persist immutable Decision Records as audit trail; MEF maintains arbitration outcome relationships (conflicts_with, supersedes, partitioned_by_scope); provides evidence density data for MAL precedence evaluation

See [Matrix Protocol Integration Diagram](MATRIX_PROTOCOL_INTEGRATION_DIAGRAM.md) for complete end-to-end integration flows.

---

## 6. Conventions and Examples

All examples in this document are **illustrative only** and do not define normative behavior.  
Normative semantics (scopes, governance, archetypes, enrich criteria) are always derived from the **MOC (Matrix Ontology Catalog)** of each organization.  
Examples are provided for clarity and MAY be adapted to local contexts, but MUST NOT be treated as protocol-level obligations.

---

## 7. Illustrative Examples (Appendix)

> **Example (Informative, MOC-dependent)**

### **Standard UKI Structure**
```yaml
# --- Illustrative Example ---
schema: "1.0"
ontology_reference: "Ontology_MEF_Support v1.0"
version: "1.0.0"

id: uki:technical:pattern:jwt-authentication  # EXAMPLE - org defines taxonomy
title: "JWT Authentication Pattern"
scope_ref: "team"           # Reference to MOC node
scope_mode: "restricted"    # or "propagated"
domain_ref: "technical"     # Reference to MOC node
type_ref: "pattern"         # Reference to MOC node
context_ref: "implementation"  # Optional if defined in MOC
maturity_ref: "validated"   # Reference to MOC node

created_date: 2025-01-25
last_modified: 2025-01-25
change_summary: "Initial version"
change_impact: "major"
status: active

content: |
  Standardized JWT authentication implementation
  following security best practices.
  
  Key components:
  - Token generation with proper expiration
  - Secure key management
  - Refresh token handling
  - Claims validation

examples:
  - input: "User login with valid credentials"
    output: "JWT token with 15-minute expiration + refresh token"
  - input: "API request with expired token"
    output: "401 Unauthorized with refresh instructions"

relationships:
  - type: depends_on
    target: uki:technical:constraint:security-requirements
    description: "Implements security requirements defined in constraint"
  
  - type: overrides
    target: uki:technical:pattern:basic-auth-deprecated
    description: "Replaces deprecated basic authentication pattern"

domain_of_influence: "engineering_teams"  # MOC organizational reference
```

### **Knowledge Promotion Example**
```yaml
# --- Illustrative Example ---
promotion:
  is_promoted_from: uki:technical:example:local-auth-impl
  promotion_rationale: |
    Solution demonstrated value across multiple projects
    and was validated by security architects.
    Promoted to organizational standard pattern.

impact_analysis:
  chain_preview:
    - uki:technical:pattern:jwt-auth → uki:technical:template:api-security → uki:technical:guideline:auth-testing
  severity: medium
  affected_domains: ["technical", "security"]
  propagation_estimate: 15

lifecycle_management_ref: "uki:org.governance:policy:lifecycle-standard"
```

### **Ontological Relationships Types**
```yaml
# --- Illustrative Example ---
relationships:
  # DEPENDENCY: This UKI requires another to function
  - type: depends_on
    target: uki:business:rule:authentication-policy
    description: "Implements organizational authentication policy"
  
  # OVERRIDE: This UKI replaces another
  - type: overrides
    target: uki:technical:pattern:basic-auth-deprecated
    description: "Replaces deprecated basic authentication pattern"
  
  # CONFLICT: This UKI cannot coexist with another
  - type: conflicts_with
    target: uki:technical:pattern:oauth-only-auth
    description: "Cannot be used simultaneously with OAuth-only authentication"
  
  # COMPLEMENT: This UKI works together with another
  - type: complements
    target: uki:technical:pattern:authorization-rbac
    description: "Works together with role-based authorization"
  
  # AMEND: This UKI modifies/extends another
  - type: amends
    target: uki:technical:pattern:basic-jwt
    description: "Extends basic JWT with refresh token capability"
  
  # PRECEDE: This UKI must be implemented before another
  - type: precedes
    target: uki:technical:pattern:api-gateway-auth
    description: "Must be implemented before API gateway authentication"
  
  # EQUIVALENT: This UKI is functionally equivalent to another
  - type: equivalent_to
    target: uki:technical:pattern:oauth2-bearer
    description: "Functionally equivalent for bearer token scenarios"
```

### **Domain and Type Examples**
```yaml
# --- Illustrative Example ---
# Different domain examples (all MOC-dependent)
domains_examples:
  technical: "uki:technical:pattern:microservice-communication"
  business: "uki:business:rule:discount-calculation"
  product: "uki:product:guideline:user-experience-standards"
  strategy: "uki:strategy:decision:technology-stack-choice"
  culture: "uki:culture:practice:code-review-process"

# Different type examples (all MOC-dependent)
types_examples:
  pattern: "Reusable solution to common problem"
  rule: "Business logic or constraint"
  guideline: "Best practice recommendation"
  template: "Structured format for specific use"
  constraint: "Limitation or requirement"
  decision: "Strategic or tactical choice made"
  example: "Concrete implementation instance"

# Different context examples (all MOC-dependent)
contexts_examples:
  discovery: "Knowledge for exploration and research"
  implementation: "Knowledge for active development"
  refinement: "Knowledge for optimization"
  qa: "Knowledge for testing and validation"
  documentation: "Knowledge for communication"
  support: "Knowledge for maintenance and troubleshooting"
```

### **Versioning and Lifecycle**
```yaml
# --- Illustrative Example ---
version_evolution:
  "1.0.0": "Initial implementation"
  "1.1.0": "Added refresh token support"
  "1.1.1": "Fixed token validation bug"
  "2.0.0": "Breaking change: new token format"

status_lifecycle:
  active: "Currently in use and maintained"
  deprecated: "Marked for removal, replacement available"
  archived: "Historical reference only, no longer maintained"

change_impact_classification:
  major: "Breaking changes requiring dependent UKI updates"
  minor: "New features, backward compatible"
  patch: "Bug fixes, no functional changes"
```

### **MEF Integration Patterns**
```yaml
# --- Illustrative Example ---
# MEF as Oracle Layer Implementation
mef_oracle_implementation:
  knowledge_structuring: "UKIs provide standardized format for all knowledge types"
  semantic_versioning: "Controlled evolution with complete traceability"
  domain_organization: "Organizational domains structure knowledge (MOC-defined)"
  validation_framework: "Automatic compliance verification"
  relationship_mapping: "Semantic connections enable intelligent navigation"

# Knowledge Sources Integration
knowledge_sources:
  governance_integration: "MEF repositories with strategic governance"
  template_configuration: "MOC-defined linkage rules"
  compliance_validation: "Strategic traceability verification"
  version_management: "Change propagation to dependent UKIs"
```

---

## 8. Cross-References

- [Matrix Protocol — Main Specification](MATRIX_PROTOCOL.md)  
- [Matrix Protocol Integration Diagram](MATRIX_PROTOCOL_INTEGRATION_DIAGRAM.md)  
- [Matrix Protocol Glossary](MATRIX_PROTOCOL_GLOSSARY.md)  
- [Matrix Protocol Integration Diagram — Portuguese](MATRIX_PROTOCOL_INTEGRATION_DIAGRAM_PT.md)  
- [Matrix Protocol Glossary — Portuguese](MATRIX_PROTOCOL_GLOSSARY_PT.md)  
- [MOC — Matrix Ontology Catalog](MOC_MATRIX_ONTOLOGY_CATALOG.md)  
- [MEP — Matrix Epistemic Principle](MEP_MATRIX_EPISTEMIC_PRINCIPLE.md)  
- [ZOF — Zion Orchestration Framework](ZOF_ZION_ORCHESTRATION_FRAMEWORK.md)  
- [OIF — Operator Intelligence Framework](OIF_OPERATOR_INTELLIGENCE_FRAMEWORK.md)  
- [MAL — Matrix Arbiter Layer](MAL_MATRIX_ARBITER_LAYER.md)  