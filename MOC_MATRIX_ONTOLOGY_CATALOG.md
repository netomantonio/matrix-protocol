# MOC — Matrix Ontology Catalog
**Acronym:** MOC  
**Status:** Stable  
**Version:** 1.0.0  
**Date:** 2025-01-25  

> 🚨 **IMPORTANT WARNING**: This document contains ILLUSTRATIVE EXAMPLES (such as `technical`, `business`, `draft`, etc.) that are NOT mandatory taxonomies. Each organization defines its own hierarchies according to their specific needs. Examples serve only as conceptual reference.

> "Local flexibility preserves global coherence."

---

## 1. Introduction

The **Matrix Ontology Catalog (MOC)** is the fundamental component that allows the Matrix Protocol to separate universal core concepts from organization-specific taxonomies and structures.

MOC defines **configurable hierarchies** for any concept that depends on organizational structures, maintaining global conceptual consistency while enabling total local adaptability.

MOC serves as the governance and configuration system that allows different organizations to adapt the Matrix Protocol to their specific structures without losing conceptual interoperability.

---

## 2. Terms and Definitions

- **Core Concepts**: Universal fixed elements of the protocol (scope, domain, maturity)
- **Local Taxonomies**: Organization-specific hierarchical structures defined by each organization
- **Configurable Hierarchies**: Classification systems adaptable to organizational needs
- **MOC Nodes**: Individual elements within a hierarchy (e.g., "team", "technical", "draft")
- **Organizational Governance**: Specific rules for authority, visibility, and propagation

Cross-reference to **organizational MOC** for specific ontological definitions.

---

## 3. Core Concepts

### Fundamental Conceptual Separation

**Core Concepts (Universal)**
- Fixed and immutable across all implementations
- Examples: scope, domain, maturity, propagation, workflow checkpoints
- Defined by the Matrix Protocol

**Local Taxonomies (Configurable)**
- Defined by the implementer in the MOC
- Examples: specific scope names, domain structure, organizational roles
- Adaptable to organizational context

### Configurable Semantic Hierarchies

Every hierarchical concept MUST:
- Be conceptually defined by the protocol
- Have its concrete hierarchy provided by the MOC
- Allow reorganization without breaking MEF, ZOF, or OIF
- Maintain stable semantic relationships

### Local Flexibility Principle
MOC ensures that organization-specific structures do not conflict with the protocol's conceptual interoperability, enabling total adaptation while maintaining global coherence.

---

## 4. Normative Rules

> ⚠️ This section is **normative**.

### Mandatory MOC Structure
Every organizational MOC MUST contain:
1. **Version metadata**: version, organization, creation/modification dates
2. **Minimum hierarchies**: scope, domain, maturity, evaluation_criteria
3. **Governance rules**: version control, audit, conflict resolution
4. **Nodes with complete metadata**: id, label, parent, level, governance

### Required Hierarchies
- **scope**: MUST define knowledge reach and visibility
- **domain**: MUST define knowledge areas and specialization  
- **maturity**: MUST define validation and reliability levels
- **evaluation_criteria**: MUST define criteria for EvaluateForEnrich checkpoint

### Integrity Rules
- Nodes MUST have unique identifiers within each hierarchy
- Parent-child relationships MUST be consistent
- Hierarchical levels MUST be sequential (0, 1, 2...)
- Governance rules MUST be defined for all nodes

### Level Semantics Configuration (Normative)

The `level` field in MOC nodes is **organizationally-defined** following MEP Principle 1 (Semantic Elasticity). Organizations MUST define their local interpretation of `level` values to enable consistent framework integration.

#### Semantic Flexibility
- **Purpose**: Each organization defines what `level` represents in their context
- **Common interpretations**: hierarchy depth, authority weight, functional priority, maturity progression
- **Framework integration**: MAL P1/P2 precedence rules MUST consult local MOC semantics
- **Local documentation**: Organizations MUST document their `level` semantics in metadata

#### Configuration Requirements
Organizations MUST provide:
- **Semantic definition**: Clear explanation of what `level` values represent
- **Ordering rules**: Whether higher/lower levels indicate precedence 
- **Framework mappings**: How MAL authority/specificity evaluation should interpret levels
- **Examples**: Concrete cases showing level usage in decision scenarios

#### Framework Integration Guidelines
- **MAL P1 (Authority Weight)**: Consult MOC to determine if higher/lower level = higher authority
- **MAL P2 (Scope Specificity)**: Consult MOC to determine if higher/lower level = more specific scope
- **ZOF Authority Validation**: Use MOC-defined level semantics for permission checks
- **OIF Contextual Filtering**: Apply organizational level interpretation for response filtering

### Change Control Rules
- MOC alterations MUST be versioned
- Impact on dependent UKIs MUST be analyzed
- Approval by competent authority MUST be mandatory
- Automatic notifications MUST be sent to affected parties

### 🔐 Authority Validation Service (Normative)

The **MOC (Matrix Ontology Catalog)** provides the canonical reference for **authority validation** in the Matrix Protocol.  
This service does not execute orchestration or decision-making (ZOF, OIF roles), but defines the **rules and ontology** required to validate whether a user MAY perform a given operation.

#### Service Interface
- **Input parameters**:  
  - `user_moc_context` (hierarchical claims: scope, domain, authority levels)  
  - `operation` (read, enrich, promote, create, update, delete)  
  - `scope_ref` (target knowledge scope)  
  - `domain_ref` (target knowledge domain)  
  - `type_ref` (target knowledge type: rule, procedure, policy, etc.)  
  - `maturity_ref` (target knowledge maturity level)  

- **Output**:  
  - `authorized: true|false` (authorization result)  
  - `required_authority` (node or level expected for authorization)  
  - `escalation_hint` (possible higher authority node for delegation/override)  
  - `moc_nodes_cited` (specific MOC nodes used in validation decision)

#### Framework Integration Requirements
- The **ZOF** MUST consume this service before enrichment (EvaluateForEnrich checkpoint)  
- The **OIF** MUST explain validation decisions to users, citing relevant MOC nodes  
- The **MEF** MUST validate UKI creation authority via this service before persisting knowledge

### 🔄 Lifecycle Management (Normative)

MOC MUST provide configuration for knowledge lifecycle management to ensure proper temporal governance of UKIs.

#### Lifecycle Configuration
```yaml
# --- Normative Configuration ---
lifecycle_management:
  default_lifecycle_policies:
    quarterly_review:                       # EXAMPLE - organization-dependent
      review_frequency_days: 90
      auto_reminder: true
      required_stakeholders: ["domain_owner", "content_author"]
      evaluation_criteria: ["accuracy", "relevance", "completeness"]
      
    annual_validation:                      # EXAMPLE - organization-dependent
      review_frequency_days: 365
      mandatory_revalidation: true
      required_evidence: ["usage_metrics", "stakeholder_feedback"]
      escalation_required: false
      
    sunset_after_2y:                       # EXAMPLE - organization-dependent
      deprecation_warning_days: 60
      final_removal_days: 730
      migration_plan_required: true
      alternative_uki_required: true
      stakeholder_notification: true
      
    continuous_monitoring:                  # EXAMPLE - organization-dependent
      monitoring_frequency_days: 30
      automated_validation: true
      threshold_triggers: ["low_usage", "conflict_frequency", "promotion_patterns"]
      
  lifecycle_transition_rules:
    draft_to_validated:
      lifecycle_change_allowed: true
      authority_escalation: false
      review_period_extension: true
      
    validated_to_deprecated:
      lifecycle_change_allowed: true
      authority_escalation: true
      mandatory_migration_plan: true
      stakeholder_approval_required: true
      
  governance_integration:
    moc_authority_validation: true          # Validate lifecycle changes via MOC authority
    mal_arbitration_lifecycle: true         # Consider lifecycle in MAL arbitration
    promotion_lifecycle_impact: true       # Analyze lifecycle impact on promotions
```

#### Lifecycle Integration Requirements
- **MEF Integration**: All UKIs MUST reference organizational lifecycle policies via lifecycle_ref
- **MAL Integration**: Lifecycle status MUST be considered in arbitration decisions
- **ZOF Integration**: Lifecycle policies MUST be evaluated during EvaluateForEnrich checkpoint
- **OIF Integration**: Lifecycle status MUST be communicated to users in explanations

> **Important**: The lifecycle examples above (`quarterly_review`, `sunset_after_2y`, etc.) are **illustrative only**. Each organization defines its own lifecycle policies according to specific governance needs while maintaining MOC structure requirements.

### ⚖️ Arbitration Policies Configuration (MAL Integration)

MOC implementations MUST provide configuration for MAL arbitration policies to ensure consistent conflict resolution.

⚠️ **MANDATORY REQUIREMENT**: This section is **REQUIRED** for all MOC implementations. Organizations MUST configure arbitration policies to ensure deterministic conflict resolution and prevent interpretation divergences.

#### Mandatory Arbitration Configuration
```yaml
# --- Normative Configuration ---
arbitration_policies:
  default_precedence_order:           # Default P1-P6 order (MAL may override)
    - "P1_authority_weight"           # Higher MOC authority wins
    - "P2_scope_specificity"          # Context-dependent scope precedence
    - "P3_maturity_level"             # validated > endorsed > draft
    - "P4_temporal_recency"           # More recent wins (respecting lifecycle)
    - "P5_evidence_density"           # More MEF evidence/references wins
    - "P6_deterministic_fallback"     # Lexicographic UKI identifier
  
  scope_specificity_rules:            # P2 configuration
    local_instructions:               # squad > tribe > org for local guidance
      precedence_order: ["squad", "tribe", "organization"]
    mandatory_rules:                  # org > tribe > squad for mandatory policies
      precedence_order: ["organization", "tribe", "squad"]
    context_mapping:
      - types: ["guideline", "example", "template"]
        rule: "local_instructions"
      - types: ["policy", "constraint", "decision"]  
        rule: "mandatory_rules"
  
  authority_weight_mapping:           # P1 configuration
    hierarchical_levels:
      - level: "organization"
        weight: 1000
        authorities: ["cto", "architecture_committee"]
      - level: "tribe"  
        weight: 500
        authorities: ["tribe_lead", "senior_architect"]
      - level: "squad"
        weight: 100
        authorities: ["squad_lead", "tech_lead", "developer"]
  
  arbitration_timeout: 2000           # Milliseconds for MAL decision
  
  conflict_type_policies:             # Specific policies per conflict type
    H1_horizontal_conflicts:
      enable_coexistence: true        # Allow scope partitioning
      require_deprecation: false      # Don't force winner-take-all
    H2_concurrent_enrichment:
      temporal_threshold_ms: 30000    # Consider concurrent if within 30s
      authority_precedence: true      # Higher authority wins in concurrent scenario
    H3_promotion_contention:
      evidence_weight_multiplier: 1.5 # External evidence gets extra weight
      cross_scope_validation: true    # Validate promotion across scope boundaries
```

#### Named Arbitration Policy Examples
```yaml
# --- Organizational Policy Examples ---
named_arbitration_policies:
  "moc:arbitration:security_conflicts":
    description: "High-authority precedence for security-critical knowledge"
    precedence_order:
      - "P1_authority_weight"         # Security requires highest authority first
      - "P3_maturity_level"           # Validated security knowledge prioritized
      - "P2_scope_specificity"        # Organization-wide security over local
      - "P4_temporal_recency"
      - "P5_evidence_density"
      - "P6_deterministic_fallback"
    authority_weight_multiplier: 2.0  # Double weight for security authorities
    maturity_minimum_required: "validated"
    
  "moc:arbitration:concurrent_enrichment":
    description: "Temporal and authority-based resolution for concurrent updates"
    precedence_order:
      - "P4_temporal_recency"         # Most recent wins in concurrent scenarios
      - "P1_authority_weight"         # Then highest authority
      - "P3_maturity_level"
      - "P2_scope_specificity"
      - "P5_evidence_density"
      - "P6_deterministic_fallback"
    temporal_window_ms: 30000         # 30-second concurrency window
    authority_tiebreaker: true
    
  "moc:arbitration:promotion_contention":
    description: "Evidence-heavy evaluation for knowledge promotion conflicts"
    precedence_order:
      - "P5_evidence_density"         # Evidence first for promotions
      - "P1_authority_weight"         # Authority validates evidence
      - "P3_maturity_level"           # Maturity progression respected
      - "P2_scope_specificity"
      - "P4_temporal_recency"
      - "P6_deterministic_fallback"
    evidence_density_multiplier: 1.5  # Extra weight for evidence
    cross_scope_validation: true
    
  "moc:arbitration:lifecycle_governance":
    description: "Lifecycle-aware precedence for knowledge evolution"
    precedence_order:
      - "P7_lifecycle_stage"          # Custom: Lifecycle takes precedence
      - "P1_authority_weight"         # Authority manages lifecycle
      - "P3_maturity_level"
      - "P2_scope_specificity"
      - "P4_temporal_recency"
      - "P5_evidence_density"
      - "P6_deterministic_fallback"
    lifecycle_respect_rules: true
    sunset_precedence: false          # Sunset knowledge doesn't win
```

#### Policy Reference Namespace Structure
```yaml
# --- Normative Namespace Specification ---
policy_reference_structure:
  namespace_format: "moc:arbitration:{policy_name}"
  
  standard_policies:                  # Common organizational policies
    - "moc:arbitration:security_conflicts"
    - "moc:arbitration:concurrent_enrichment"
    - "moc:arbitration:promotion_contention"
    - "moc:arbitration:lifecycle_governance"
    - "moc:arbitration:cross_domain_resolution"
    
  custom_policy_naming:
    format: "moc:arbitration:{organization}_{domain}_{purpose}"
    examples:
      - "moc:arbitration:acme_technical_reviews"
      - "moc:arbitration:corp_business_policies"
      - "moc:arbitration:startup_rapid_iteration"
      
  policy_inheritance:
    default_fallback: "default_precedence_order"
    policy_override: "named policy completely replaces default"
    policy_extension: "named policy modifies specific precedence rules"
```

#### MAL Integration Requirements
- MAL MUST consult MOC arbitration policies for precedence rule application
- MOC scope specificity rules MUST be applied for P2 evaluation
- MOC authority hierarchies MUST be used for P1 weight calculation
- Arbitration timeout MUST be enforced by MAL
- Policy changes MUST trigger MAL configuration updates

### 🔄 Taxonomy Evolution Feedback (Normative)

MOC MUST implement feedback mechanisms for taxonomic updates based on UKI promotion patterns.

#### Promotion Pattern Analysis
```yaml
# --- Normative Configuration ---
promotion_analysis:
  monitoring_window_days: 90              # Analysis window for promotion patterns
  promotion_threshold_triggers:
    frequent_promotions:                   # Many promotions of same type
      min_count: 10
      same_source_scope: true
      same_target_scope: true
      action: "suggest_taxonomy_refinement"
    
    cross_scope_patterns:                  # Promotions crossing hierarchies
      pattern_frequency: 5
      cross_boundary_type: ["scope", "domain"]
      action: "analyze_taxonomy_gaps"
    
    authority_escalation_frequency:        # Frequent escalations
      escalation_count: 8
      time_window_days: 30
      action: "review_authority_hierarchy"
```

#### Feedback Loop for Taxonomic Evolution
- **Automatic Detection**: System MUST monitor promotion patterns and identify taxonomic inconsistencies
- **Impact Analysis**: MOC MUST analyze how successive promotions indicate hierarchical gaps or misalignments
- **Evolution Proposals**: System MUST generate taxonomic refinement proposals based on usage evidence
- **Governed Approval**: Taxonomic changes MUST follow organizational approval process
- **Controlled Migration**: MOC updates MUST include migration plan for existing UKIs

#### Criteria for Taxonomic Evolution
```yaml
# --- Normative Criteria ---
evolution_criteria:
  taxonomy_refinement_indicators:
    - "Frequent promotions from squad → tribe → org (suggests missing intermediate level)"
    - "Cross-domain promotions indicating domain boundary issues"
    - "Authority escalations suggesting hierarchy gaps"
    - "Semantic conflicts in MAL indicating taxonomy overlap"
  
  evolution_validation_requirements:
    - "Impact analysis on existing UKIs"
    - "Migration path definition for affected knowledge"
    - "Stakeholder approval across affected hierarchical levels"
    - "Rollback plan in case of evolution issues"
```

#### 🧬 Ontology Evolution (Normative)

**Core Principle**: Successive UKI promotions provide feedback for taxonomic refinement, but taxonomic changes are NEVER automatic. MOC remains the single source of truth for organizational ontologies.

##### Promotion ↔ Ontology Feedback Loop
```yaml
# --- Normative Configuration ---
ontology_evolution:
  feedback_mechanism:
    promotion_pattern_detection:       # Automatic detection
      enabled: true
      analysis_frequency_days: 30
      pattern_threshold_analysis: true
      
    taxonomy_suggestion_generation:    # Automatic proposals
      enabled: true
      evidence_aggregation: true
      impact_pre_analysis: true
      stakeholder_identification: true
      
    ontology_update_authority:         # Manual curatorial control
      automatic_updates: false         # NEVER automatic
      curatorial_approval_required: true
      organizational_governance: true
      change_impact_validation: true

  curatorial_governance:
    approval_authority: ["architecture_committee", "ontology_curators"]
    evidence_review_required: true
    stakeholder_consultation: true
    controlled_migration_planning: true
    rollback_capability_required: true
    
  framework_separation:
    mef_role: "promotion_registration"    # MEF registers promotions only
    mal_role: "conflict_arbitration"      # MAL arbitrates conflicts only  
    moc_role: "taxonomic_authority"       # MOC is single source of truth
    promotion_feedback_flow: "mef → analysis → proposals → moc_curation"
```

##### Evolution Guarantees
- **No Contradiction**: Promotion is MEF registration; taxonomy is MOC authority
- **Curatorial Control**: All taxonomic changes require organizational approval
- **Evidence-Based**: Promotion patterns inform but never automatically change taxonomies  
- **Controlled Migration**: Changes include impact analysis and migration plans
- **Framework Integrity**: Clear separation between promotion registration and taxonomic authority

---

## 5. Interoperability

MOC serves as the governance foundation that enables organizational customization across all frameworks:

- **MEF (Matrix Embedding Framework)**: Validates all *_ref field references against MOC hierarchies; enforces organizational taxonomy constraints; provides governance rules for UKI creation and promotion workflows
- **ZOF (Zion Orchestration Framework)**: Supplies evaluation criteria for EvaluateForEnrich checkpoint; validates user authority for enrichment operations; defines organizational workflow governance rules; invokes MAL with MOC-configured arbitration policies
- **OIF (Operator Intelligence Framework)**: Provides hierarchical context for intelligence filtering; validates user authority for archetype operations; supplies escalation paths for authority requirements; uses MOC nodes in arbitration explanations
- **MEP (Matrix Epistemic Principle)**: Implements organizational context for derived authority; provides taxonomic foundation for epistemological stratification; enables local flexibility with global coherence
- **MAL (Matrix Arbiter Layer)**: Consumes MOC arbitration policies for precedence rule configuration; applies MOC authority hierarchies for P1 evaluation; uses MOC scope specificity rules for P2 evaluation; respects MOC timeout and conflict type policies

See [Matrix Protocol Integration Diagram](MATRIX_PROTOCOL_INTEGRATION_DIAGRAM.md) for MOC validation and governance flows.

---

## 6. Conventions and Examples

All examples in this document are **illustrative only** and do not define normative behavior.  
Normative semantics (scopes, governance, archetypes, enrich criteria) are always derived from the **MOC (Matrix Ontology Catalog)** of each organization.  
Examples are provided for clarity and MAY be adapted to local contexts, but MUST NOT be treated as protocol-level obligations.

---

## 7. Illustrative Examples (Appendix)

> **Example (Informative, MOC-dependent)**

### **Base MOC Structure**
```yaml
# --- Illustrative Example ---
moc_version: "1.0"
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
      - id: "personal"    # EXAMPLE - each org defines their scopes
        label: "Personal"
        parent: null
        level: 0
        governance:
          visibility: ["owner"]
          propagation: "none"
          authority_required: "self"
      - id: "team"        # EXAMPLE - each org defines their scopes
        label: "Team"
        parent: "personal"
        level: 1
        governance:
          visibility: ["team_members"]
          propagation: "restricted"
          authority_required: "team_lead"
      - id: "organization" # EXAMPLE - each org defines their scopes
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
      - id: "technical"    # EXAMPLE - each org defines their domains
        label: "Technical"
        parent: null
        level: 0
        governance:
          owners: ["engineering"]
          reviewers: ["tech_leads", "architects"]
      - id: "business"     # EXAMPLE - each org defines their domains
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
      - id: "draft"        # EXAMPLE - each org defines their maturity levels
        label: "Draft"
        parent: null
        level: 0
        governance:
          auto_promotion: false
          validation_required: false
      - id: "review"       # EXAMPLE - each org defines their maturity levels
        label: "Review"
        parent: "draft"
        level: 1
        governance:
          auto_promotion: false
          validation_required: true
          reviewers_required: 2
      - id: "approved"     # EXAMPLE - each org defines their maturity levels
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
      - id: "relevance"    # EXAMPLE - each org defines their criteria
        label: "Relevance"
        parent: null
        level: 0
        governance:
          threshold: "medium"
          evaluators: ["domain_experts"]
      - id: "reusability"  # EXAMPLE - each org defines their criteria
        label: "Reusability"
        parent: null
        level: 0
        governance:
          threshold: "high"
          evaluators: ["architects"]

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

### **MEF Integration**
```yaml
# --- Illustrative Example ---
# MOC Fields in MEF:
scope_ref: "team"           # Reference to MOC node
scope_mode: "restricted"    # or "propagated"
domain_ref: "technical"     # Reference to MOC node
type_ref: "pattern"         # Reference to MOC node
maturity_ref: "approved"    # Reference to MOC node

# Automatic Resolution:
# - System consults MOC to validate references
# - Applies governance rules automatically
# - Propagates changes according to configuration
```

### **ZOF Integration**
```yaml
# --- Illustrative Example ---
# EvaluateForEnrich Checkpoint:
flow_execution:
  - state: "evaluate_for_enrich"
    signals:
      context: "Evaluating if generated knowledge should enrich Oracle"
      criteria_refs: ["relevance", "reusability", "impact"]  # MOC references
      decision: "Based on organization-specific MOC criteria"
      result: "Approved for enrichment with 'team' scope"
```

### **OIF Integration**
```yaml
# --- Illustrative Example ---
# Access Control:
user_context:
  scope_level: "team" 
  domain_access: ["technical", "business"]
  
access_control:
  uki_filtering: "based on user's scope_ref and domain_ref"
  explanation_refs: "references specific MOC nodes in justifications"
```

### **Change Control Process**
```yaml
# --- Illustrative Example ---
change_process:
  impact_analysis:
    - node_addition: "Low impact, backward compatible"
    - hierarchy_modification: "Medium impact, validation required"
    - node_removal: "High impact, mandatory dependency analysis"
  
  update_process:
    1: "Change proposal with impact analysis"
    2: "Dependent UKI validation"
    3: "Approval by competent authority"
    4: "Versioning and notification"
    5: "Migration period for dependents"
```

**Benefits Examples:**
- *Total Flexibility*: Adapt structures to specific organizational needs
- *Transparent Governance*: Clear and auditable rules for changes
- *Organic Evolution*: Organizational changes don't break the protocol
- *Interoperability*: Different organizations can share knowledge
- *Rich AI Context*: AI understands specific organizational hierarchies

---

## 8. Cross-References

- [Matrix Protocol — Main Specification](MATRIX_PROTOCOL.md)  
- [Matrix Protocol Integration Diagram](MATRIX_PROTOCOL_INTEGRATION_DIAGRAM.md)  
- [Matrix Protocol Glossary](MATRIX_PROTOCOL_GLOSSARY.md)  
- [Matrix Protocol Integration Diagram — Portuguese](MATRIX_PROTOCOL_INTEGRATION_DIAGRAM_PT.md)  
- [Matrix Protocol Glossary — Portuguese](MATRIX_PROTOCOL_GLOSSARY_PT.md)  
- [MEF — Matrix Embedding Framework](MEF_MATRIX_EMBEDDING_FRAMEWORK.md)  
- [ZOF — Zion Orchestration Framework](ZOF_ZION_ORCHESTRATION_FRAMEWORK.md)  
- [OIF — Operator Intelligence Framework](OIF_OPERATOR_INTELLIGENCE_FRAMEWORK.md)  
- [MEP — Matrix Epistemic Principle](MEP_MATRIX_EPISTEMIC_PRINCIPLE.md)  
- [MAL — Matrix Arbiter Layer](MAL_MATRIX_ARBITER_LAYER.md)  