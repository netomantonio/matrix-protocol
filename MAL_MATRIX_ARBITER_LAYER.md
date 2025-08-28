# MAL — Matrix Arbiter Layer
**Acronym:** MAL  
**Status:** Draft  
**Version:** 1.0.0  
**Date:** 2025-08-26  

> "In the absence of conflict, wisdom remains untested." — Ancient Proverb

---

## 1. Introduction

The **Matrix Arbiter Layer (MAL)** is the protocol's conflict and concurrency arbitration layer that operates as the final decision-making authority when local governance rules cannot resolve complex conflicts.

MAL is invoked **only** when local rules (scope filtering, authority validation, EvaluateForEnrich) cannot resolve three specific conflict types: horizontal conflicts between equivalent UKIs, concurrent enrichment attempts, and promotion contentions.

MAL does not replace MOC, ZOF, OIF, or MEF; it provides deterministic decision-making, then delegates explanation to OIF and persistence to MEF while respecting MOC-configured policies.

---

## 2. Terms and Definitions

- **Arbitration Event**: A normalized input describing a conflict or concurrency condition requiring MAL decision
- **Decision Record**: A signed, immutable outcome with winner/loser designation, rationale, and references
- **Precedence Policy**: Ordered tie-break rules configured in MOC with MAL-provided defaults
- **Horizontal Conflict (H1)**: Two or more UKIs of equivalent scope level that conflict semantically
- **Concurrent Enrichment (H2)**: Two or more flows attempting to enrich overlapping semantics simultaneously
- **Promotion Contention (H3)**: Competing proposals to promote distinct UKIs to higher governance level

Cross-reference to **MOC (Matrix Ontology Catalog)** for organization-specific arbitration policies.

---

## 3. Core Concepts

### No-Op Principle
MAL operates as a last resort arbitration layer. If scope/authority rules can resolve conflicts locally through standard MOC validation, MAL MUST NOT be invoked.

### Deterministic Decision-Making
Given identical inputs and policy configuration, MAL MUST produce consistent, reproducible decisions across all invocations to ensure system predictability.

### Epistemic Rationale Integration
Every MAL decision MUST include epistemological justification aligned with MEP principles, referencing specific MOC nodes and providing traceable reasoning.

### Auditability and Transparency
All arbitration decisions MUST be persisted as immutable Decision Records with complete traceability to input UKIs, MOC policies, and reasoning chains.

### Non-blocking User Experience
If MAL cannot decide within the configured arbitration_timeout, ZOF MUST apply the safe default outcome:
- Outcome = no enrich
- Status = pending arbitration

OIF MUST notify the user that arbitration is pending, including escalation instructions from the MOC if available.

---

## 4. Normative Rules

> ⚠️ This section is **normative**.

### Mandatory Invocation Conditions
ZOF MUST invoke MAL when it detects conflict types H1, H2, or H3 after EvaluateForEnrich checkpoint completion and local resolution attempts have failed.

### Arbitration Authority Boundaries
- MAL MUST make final decisions on conflicts within its scope
- MAL MUST NOT communicate outcomes directly to users
- OIF MUST NOT attempt arbitration; it MUST only explain MAL outcomes
- OIF MUST render all MAL outcomes using an Arbitration Explanation Template that includes at least:
  - decision_id
  - outcome
  - winner/losers (if applicable)
  - precedence_applied
  - epistemic_rationale with moc_nodes cited
- MEF MUST persist all MAL decisions as immutable Decision Records
- MOC MUST provide policy configuration but MUST NOT override MAL decisions

### Normalized Input Requirements
Every Arbitration Event MUST contain:
- **event_id**: Unique identifier for the arbitration request
- **event_type**: One of {H1, H2, H3} indicating conflict classification
- **candidates[]**: Array of conflicting UKI references with complete metadata
- **user_moc_context**: User's hierarchical claims and authority levels
- **operation**: Requested operation type (read/enrich/promote)
- **policy_ref**: Optional reference to specific MOC arbitration policy

### Precedence Policy Hierarchy

MAL MUST apply precedence rules as configured in the MOC.

If policy_ref is provided in the Arbitration Event, MAL MUST resolve using the referenced policy from the MOC.

If absent, MAL MAY fallback to its canonical default precedence (P1–P6).

Organizations SHOULD always configure arbitration policies in the MOC to override defaults.

Canonical default precedence order:
1. **P1 Authority Weight**: Higher authority node in MOC hierarchy wins
2. **P2 Scope Specificity**: More specific scope wins for local instructions; broader scope wins for mandatory global rules
3. **P3 Maturity Level**: validated > endorsed > draft/experimental
4. **P4 Temporal Recency**: More recent version wins if not violating lifecycle rules
5. **P5 Evidence Density**: UKI with more MEF evidence links and references
6. **P6 Deterministic Fallback**: Lexicographic UKI identifier comparison

### Decision Outcomes
MAL MUST produce one of four outcomes:
- **winner**: Single UKI chosen as authoritative
- **coexist**: Multiple UKIs valid through scope partitioning
- **reject_all**: None satisfies policy requirements
- **defer**: Requires human override or escalation

### Persistence and Communication Requirements

MAL MUST NOT introduce ontological terms outside of the MOC.

All outcomes must reference existing ontology fields:
- scope_ref (partitioning)
- authority_ref (authority hierarchy)  
- lifecycle_ref (promotion/deprecation rules)

Relationships (conflicts_with, supersedes) MUST be persisted in the MEF, always citing MOC references.

- MEF MUST store Decision Records with conflict relationships using MOC ontological terms
- OIF MUST receive structured messages to explain decisions using Arbitration Explanation Templates
- Arbitration Explanation Templates MUST include minimum required fields: decision_id, outcome, winner/losers, precedence_applied, epistemic_rationale with moc_nodes cited
- All decisions MUST include epistemic rationale referencing MOC nodes and MEF evidence

### Time Constraints and Consistency
- MAL MUST complete arbitration within arbitration_timeout configured in MOC
- If MAL cannot decide within the configured arbitration_timeout, ZOF MUST apply the safe default outcome:
  - Outcome = no enrich
  - Status = pending arbitration
- OIF MUST notify the user that arbitration is pending, including escalation instructions from the MOC if available
- Decision Records MUST be immutable once persisted

---

## 5. Interoperability

MAL operates as the arbitration nexus integrating decision-making across all Matrix Protocol frameworks:

- **MEF (Matrix Embedding Framework)**: Persists Decision Records as immutable audit trail; maintains conflict relationship metadata; provides evidence density calculations for precedence evaluation
- **ZOF (Zion Orchestration Framework)**: Detects H1/H2/H3 conditions during EvaluateForEnrich; invokes MAL with normalized Arbitration Events; applies MAL decisions through workflow actions
- **OIF (Operator Intelligence Framework)**: Renders MAL decisions to users via Arbitration Explanation templates; maintains epistemic humility by not overriding MAL determinations; provides contextual explanations
- **MOC (Matrix Ontology Catalog)**: Provides arbitration policies and precedence rule configuration; supplies authority hierarchy for P1 evaluation; defines scope specificity rules for P2 evaluation
- **MEP (Matrix Epistemic Principle)**: Guides epistemic rationale generation; ensures derived authority principles in decision explanations; mandates explainability in arbitration outcomes

See [Matrix Protocol Integration Diagram](MATRIX_PROTOCOL_INTEGRATION_DIAGRAM.md) for MAL arbitration workflow patterns.

---

## 6. Conventions and Examples

All examples in this document are **illustrative only** and do not define normative behavior.  
Normative semantics (scopes, governance, archetypes, enrich criteria) are always derived from the **MOC (Matrix Ontology Catalog)** of each organization.  
Examples are provided for clarity and MAY be adapted to local contexts, but MUST NOT be treated as protocol-level obligations.

---

## 7. Illustrative Examples (Appendix)

> **Example (Informative, MOC-dependent)**

### **Horizontal Conflict (H1) Arbitration**
```yaml
# --- Illustrative Example ---
arbitration_event:
  event_id: "mal-evt-20250826-001"
  event_type: "H1"
  conflict_description: "Two equivalent-scope security rules conflict"
  
  candidates:
    - uki_ref: "uki:squad-x:rule:data-retention-30d"
      scope_ref: "squad-x"
      domain_ref: "security"
      type_ref: "rule"
      maturity_level: "validated"
      version: "1.2.0"
      evidence_refs: ["uki:org:policy:gdpr-compliance", "doc:audit-logs-2024"]
      timestamps:
        created_at: "2025-08-15T10:00:00Z"
        updated_at: "2025-08-20T14:30:00Z"
    
    - uki_ref: "uki:squad-x:rule:data-retention-7d"
      scope_ref: "squad-x"
      domain_ref: "security"
      type_ref: "rule"
      maturity_level: "endorsed"
      version: "2.0.0"
      evidence_refs: ["uki:org:policy:data-minimization"]
      timestamps:
        created_at: "2025-08-22T09:15:00Z"
        updated_at: "2025-08-22T09:15:00Z"
  
  user_moc_context:
    scopes: ["squad-x", "tribe-alpha", "organization"]
    authority_level: "squad_lead"
    domain_access: ["security", "compliance"]
  
  operation: "enrich"
  policy_ref: "moc:arbitration:security_conflicts"

decision_record:
  decision_id: "mal-dec-20250826-h1-001"
  event_ref: "mal-evt-20250826-001"
  outcome: "winner"
  
  winner: "uki:squad-x:rule:data-retention-30d"
  losers: ["uki:squad-x:rule:data-retention-7d"]
  
  precedence_applied:
    - "P1_authority": "Both equivalent squad-level"
    - "P3_maturity": "validated > endorsed"
    - "P5_evidence": "GDPR compliance trumps data minimization in security context"
  
  actions:
    - "mark_conflict"
    - "deprecate:uki:squad-x:rule:data-retention-7d"
    - "gate_enrich"
  
  epistemic_rationale:
    summary: "Validated maturity and stronger regulatory evidence"
    reasoning: |
      While both UKIs operate at equivalent squad scope, the 30-day retention rule
      demonstrates higher epistemological maturity (validated vs endorsed) and 
      stronger regulatory evidence linking to GDPR compliance requirements.
    references:
      moc_nodes: 
        - "moc:maturity:validated"
        - "moc:domain:security:regulatory_priority"
      mef_evidence:
        - "uki:org:policy:gdpr-compliance"
        - "doc:audit-logs-2024"
  
  audit:
    decided_at: "2025-08-26T15:45:30Z"
    decided_by: "MAL:v1.0.0"
    timeout_used_ms: 150
    precedence_policy: "moc:arbitration:security_conflicts"
  
  oif_message:
    template: "arbitration_explanation_h1"
    summary: "Conflict resolved: 30-day retention rule chosen over 7-day rule"
    reason_code: "MATURITY_AND_EVIDENCE_PRIORITY"
    next_steps: "7-day rule deprecated; review migration path"
```

### **Concurrent Enrichment (H2) Arbitration**
```yaml
# --- Illustrative Example ---
arbitration_event:
  event_id: "mal-evt-20250826-002"
  event_type: "H2"
  conflict_description: "Simultaneous enrichment attempts on authentication patterns"
  
  candidates:
    - flow_id: "zof-auth-jwt-implementation-001"
      uki_target: "uki:technical:pattern:jwt-authentication"
      user_context: 
        user_id: "dev-alice"
        scope: "squad-frontend"
        authority: "developer"
      proposed_changes: "Add OAuth2 integration details"
      timestamp: "2025-08-26T16:20:00Z"
    
    - flow_id: "zof-auth-jwt-implementation-002"
      uki_target: "uki:technical:pattern:jwt-authentication"
      user_context:
        user_id: "dev-bob"
        scope: "squad-backend"
        authority: "tech_lead"
      proposed_changes: "Update security requirements"
      timestamp: "2025-08-26T16:20:15Z"
  
  operation: "concurrent_enrich"
  policy_ref: "moc:arbitration:concurrent_enrichment"

decision_record:
  decision_id: "mal-dec-20250826-h2-001"
  event_ref: "mal-evt-20250826-002"
  outcome: "winner"
  
  winner: "zof-auth-jwt-implementation-002"
  losers: ["zof-auth-jwt-implementation-001"]
  
  precedence_applied:
    - "P1_authority": "tech_lead > developer"
    - "P4_temporal": "15-second difference negligible"
  
  actions:
    - "allow_enrich:zof-auth-jwt-implementation-002"
    - "defer_enrich:zof-auth-jwt-implementation-001"
    - "require_review:merge_oauth2_changes_later"
  
  epistemic_rationale:
    summary: "Higher authority precedence in concurrent scenario"
    reasoning: |
      When concurrent enrichment attempts occur within temporal threshold,
      authority precedence takes priority. Tech lead authority supersedes
      developer authority for critical authentication patterns.
    references:
      moc_nodes:
        - "moc:authority:tech_lead"
        - "moc:domain:technical:authentication_critical"
  
  audit:
    decided_at: "2025-08-26T16:20:30Z"
    decided_by: "MAL:v1.0.0"
    timeout_used_ms: 75
```

### **Promotion Contention (H3) Arbitration**
```yaml
# --- Illustrative Example ---
arbitration_event:
  event_id: "mal-evt-20250826-003"
  event_type: "H3"
  conflict_description: "Competing promotion proposals to organizational level"
  
  candidates:
    - uki_ref: "uki:squad-x:guideline:code-review-process"
      current_scope: "squad-x"
      proposed_scope: "organization"
      promotion_rationale: "Successful 6-month implementation across 3 squads"
      evidence_refs: ["metrics:code-quality-improvement-30pct"]
      promoted_by: "squad_lead_alice"
    
    - uki_ref: "uki:tribe-alpha:guideline:code-review-standard"
      current_scope: "tribe-alpha"
      proposed_scope: "organization"
      promotion_rationale: "Compliance with industry standards and audit requirements"
      evidence_refs: ["audit:external-compliance-2025", "standard:iso-27001"]
      promoted_by: "tribe_lead_charlie"
  
  operation: "promote"
  policy_ref: "moc:arbitration:promotion_contention"

decision_record:
  decision_id: "mal-dec-20250826-h3-001"
  event_ref: "mal-evt-20250826-003"
  outcome: "winner"
  
  winner: "uki:tribe-alpha:guideline:code-review-standard"
  losers: ["uki:squad-x:guideline:code-review-process"]
  
  precedence_applied:
    - "P1_authority": "tribe_lead > squad_lead for org-level promotions"
    - "P2_scope": "tribe-level closer to org-level than squad-level"
    - "P5_evidence": "External compliance audit carries higher weight"
  
  actions:
    - "promote:uki:tribe-alpha:guideline:code-review-standard:organization"
    - "merge_evidence:uki:squad-x:guideline:code-review-process:metrics"
    - "deprecate:uki:squad-x:guideline:code-review-process"
  
  epistemic_rationale:
    summary: "Authority, scope proximity, and compliance evidence convergence"
    reasoning: |
      Tribe-level promotion proposals demonstrate higher organizational
      alignment for org-level scope. External compliance evidence provides
      stronger epistemological foundation than internal metrics alone.
    references:
      moc_nodes:
        - "moc:authority:tribe_lead:promotion_rights"
        - "moc:scope:organization:compliance_requirements"
      mef_evidence:
        - "audit:external-compliance-2025"
        - "standard:iso-27001"
  
  audit:
    decided_at: "2025-08-26T17:10:45Z"
    decided_by: "MAL:v1.0.0"
    timeout_used_ms: 200
```

### **Coexistence Decision**
```yaml
# --- Illustrative Example ---
arbitration_event:
  event_id: "mal-evt-20250826-004"
  event_type: "H1"
  conflict_description: "Domain-specific implementations of similar patterns"

decision_record:
  decision_id: "mal-dec-20250826-h1-002"
  outcome: "coexist"
  
  coexist_ukis:
    - "uki:frontend:pattern:authentication-spa"
    - "uki:backend:pattern:authentication-api"
  
  precedence_applied:
    - "P2_scope": "Domain specificity allows coexistence"
    - "P5_evidence": "Different technical contexts require different approaches"
  
  actions:
    - "partition_scope_ref:domain_specific"
    - "add_relationship:complements"
    - "require_consistency:security_principles"
  
  epistemic_rationale:
    summary: "Domain separation enables complementary coexistence"
    reasoning: |
      Frontend SPA and backend API authentication patterns address
      different technical contexts with complementary approaches.
      Coexistence preserves domain-specific expertise while ensuring
      security principle consistency.
```

---

## 8. MAL Minimal Interfaces (Normative)

### Arbitration Event Input Schema
```yaml
# --- Normative Interface ---
arbitration_event:
  event_id: string                    # Required: Unique arbitration identifier
  event_type: enum[H1, H2, H3]        # Required: Conflict classification
  timestamp: ISO8601                  # Required: Event creation timestamp
  
  candidates: array                   # Required: Conflicting entities
    - uki_ref: string                 # UKI identifier
      scope_ref: string               # MOC scope reference
      domain_ref: string              # MOC domain reference  
      type_ref: string                # UKI type reference
      maturity_level: string          # Maturity classification
      version: semver                 # Version identifier
      evidence_refs: array[string]    # Supporting evidence references
      timestamps:
        created_at: ISO8601
        updated_at: ISO8601
  
  user_moc_context:                   # Required: User context
    scopes: array[string]             # User's scope hierarchy
    authority_level: string           # User's authority designation
    domain_access: array[string]      # Accessible domains
  
  operation: enum[read, enrich, promote]  # Required: Requested operation
  policy_ref: string                  # Optional: Specific arbitration policy
  
  metadata:                           # Optional: Additional context
    initiating_flow: string           # ZOF flow identifier
    conflict_detected_at: ISO8601     # When conflict was identified
    previous_attempts: integer        # Failed local resolution attempts
```

### Decision Record Output Schema
```yaml
# --- Normative Interface ---
decision_record:
  decision_id: string                 # Required: Unique decision identifier
  event_ref: string                   # Required: Reference to arbitration event
  timestamp: ISO8601                  # Required: Decision timestamp
  
  outcome: enum[winner, coexist, reject_all, defer]  # Required: Decision result
  
  winner: string                      # Conditional: UKI chosen (if outcome=winner)
  losers: array[string]               # Conditional: Defeated UKIs (if applicable)
  coexist_ukis: array[string]         # Conditional: Valid UKIs (if outcome=coexist)
  
  precedence_applied: array           # Required: Applied precedence rules
    - rule_id: enum[P1, P2, P3, P4, P5, P6]
      description: string
      evaluation: string
  
  actions: array[string]              # Required: Actions to be executed
  
  epistemic_rationale:                # Required: MEP-aligned explanation
    summary: string                   # Brief decision rationale
    reasoning: string                 # Detailed explanation
    references:
      moc_nodes: array[string]        # Referenced MOC nodes
      mef_evidence: array[string]     # Referenced MEF evidence
  
  audit:                              # Required: Audit information
    decided_at: ISO8601               # Decision timestamp
    decided_by: string                # MAL version identifier
    timeout_used_ms: integer          # Processing time used
    precedence_policy: string         # Applied policy reference
  
  oif_message:                        # Required: User explanation data
    template: string                  # OIF template identifier
    summary: string                   # User-facing summary
    reason_code: string               # Structured reason code
    next_steps: string                # Recommended actions
```

---

## 9. Cross-References

- [Matrix Protocol — Main Specification](MATRIX_PROTOCOL.md)  
- [Matrix Protocol Integration Diagram](MATRIX_PROTOCOL_INTEGRATION_DIAGRAM.md)  
- [Matrix Protocol Glossary](MATRIX_PROTOCOL_GLOSSARY.md)  
- [Matrix Protocol Integration Diagram — Portuguese](MATRIX_PROTOCOL_INTEGRATION_DIAGRAM_PT.md)  
- [Matrix Protocol Glossary — Portuguese](MATRIX_PROTOCOL_GLOSSARY_PT.md)  
- [MEF — Matrix Embedding Framework](MEF_MATRIX_EMBEDDING_FRAMEWORK.md)  
- [ZOF — Zion Orchestration Framework](ZOF_ZION_ORCHESTRATION_FRAMEWORK.md)  
- [OIF — Operator Intelligence Framework](OIF_OPERATOR_INTELLIGENCE_FRAMEWORK.md)  
- [MOC — Matrix Ontology Catalog](MOC_MATRIX_ONTOLOGY_CATALOG.md)  
- [MEP — Matrix Epistemic Principle](MEP_MATRIX_EPISTEMIC_PRINCIPLE.md)  