# MEF Support Ontology — Matrix Embedding Framework Support Ontology
**Acronym:** MEF Support Ontology  
**Status:** Stable  
**Version:** 1.0.0  
**Date:** 2025-01-25  

> 🚨 **IMPORTANT WARNING**: This document contains **ILLUSTRATIVE EXAMPLES ONLY** (such as `technical`, `business`, `draft`, etc.) that are NOT mandatory taxonomies. The **MOC (Matrix Ontology Catalog)** is the only definitive source for organizational taxonomies.

---

## 1. Introduction

The **MEF Support Ontology** defines reference controlled vocabularies that can be used in UKI structures, serving as a starter set for organizations implementing the Matrix Embedding Framework.

This document provides illustrative examples of domains, types, relationships, and other structural elements that organizations can use as a starting point when configuring their own organizational MOC.

It is important to emphasize that these are **reference examples**, not mandatory taxonomies.

---

## 2. Terms and Definitions

- **Controlled Vocabularies**: Standardized term sets to ensure consistency
- **Starter Set**: Initial example set to facilitate implementation
- **Reference Domains**: Examples of organizational knowledge areas
- **UKI Types**: Structural categories of knowledge units
- **Ontological Relationships**: Semantic connections between UKIs
- **Severity Levels**: Impact classifications for changes
- **Lifecycle States**: Status progression of knowledge units

Cross-reference to **organizational MOC** for specific validated taxonomies.

---

## 3. Core Concepts

### Principle of Organizational Flexibility
All elements in this document are **configurable suggestions**:
- Organizations can use as foundation
- Can add specific elements
- Can modify or remove as needed
- Must define their own hierarchies in MOC

### Separation of Reference vs Implementation
- **This Document**: Illustrative examples and guidance
- **Organizational MOC**: Specific authoritative definitions
- **Implementations**: Must consult MOC, not this document

### Vocabulary Categories
This ontology covers five main categories:
- **Reference Domains**: Example knowledge areas
- **UKI Types**: Structural knowledge categories
- **Relationship Types**: Semantic connection types
- **Severity Levels**: Impact classification system
- **Lifecycle States**: Knowledge unit status progression

---

## 4. Normative Rules

> ⚠️ This section is **normative**.

### Reference Vocabulary Usage
- Organizations MAY use examples in this document as starting point
- Organizations MUST define their specific vocabularies in organizational MOC
- Systems MUST validate UKI fields against organizational MOC, not this document
- Implementations MUST treat this document as illustrative reference only

### Controlled Extensibility
- Vocabularies MAY be extended through organizational MOC
- Semantic validation MUST be centralized in MOC
- Changes MUST follow defined organizational governance process

### Validation Requirements
- Automated systems MUST validate UKI fields based on MOC-defined vocabularies
- All UKI field values MUST reference valid nodes in organizational MOC
- Cross-references between UKIs MUST be validated against MOC relationship rules

---

## 5. Interoperability

- **MEF (Matrix Embedding Framework)**: Uses vocabularies defined in organizational MOC
- **MOC (Matrix Ontology Catalog)**: Authoritative source for all organizational vocabularies
- **ZOF (Zion Orchestration Framework)**: Consults vocabularies during EvaluateForEnrich checkpoint
- **OIF (Operator Intelligence Framework)**: Applies vocabularies in filtering and explanations

---

## 6. Conventions and Examples

All examples in this document are **illustrative only** and do not define normative behavior.  
Normative semantics (scopes, governance, archetypes, enrich criteria) are always derived from the **MOC (Matrix Ontology Catalog)** of each organization.  
Examples are provided for clarity and MAY be adapted to local contexts, but MUST NOT be treated as protocol-level obligations.

---

## 7. Illustrative Examples (Appendix)

> **Example (Informative, MOC-dependent)**

### **Reference Domains**
```yaml
# --- Illustrative Examples ---
reference_domains:
  strategy:
    description: "High-level decisions, strategic planning"
    area_of_influence: "Organizational direction, long-term objectives"
    
  operations:
    description: "Operational processes, execution and procedures"
    area_of_influence: "Workflows, task execution"
    
  security:
    description: "Security, protection and risk management"
    area_of_influence: "Access controls, vulnerability management"
    
  governance:
    description: "Governance, control and oversight"
    area_of_influence: "Control structures, organizational oversight"
    
  communication:
    description: "Communication, collaboration and relationships"
    area_of_influence: "Communication protocols, information flows"

# Your organization can use completely different terms:
alternative_domain_examples:
  innovation: "Innovation processes and research"
  quality: "Quality management and continuous improvement"
  sustainability: "Sustainable practices and environmental responsibility"
  customer_experience: "Customer experience management"
  data_governance: "Data management and governance"
```

### **UKI Type References**
```yaml
# --- Illustrative Examples ---
reference_types:
  pattern:
    description: "Reusable solution to common problem"
    typical_content: "Implementation approaches, architectural solutions"
    
  rule:
    description: "Business logic or constraint"
    typical_content: "Validation logic, business constraints"
    
  guideline:
    description: "Best practice recommendation"
    typical_content: "Recommended approaches, standards"
    
  template:
    description: "Structured format for specific use"
    typical_content: "Document templates, code scaffolding"
    
  constraint:
    description: "Limitation or requirement"
    typical_content: "System limitations, regulatory requirements"
    
  decision:
    description: "Strategic or tactical choice made"
    typical_content: "Architecture decisions, policy choices"
    
  example:
    description: "Concrete implementation instance"
    typical_content: "Code examples, implementation samples"

# Your organization can use specific categories:
alternative_type_examples:
  procedure: "Standardized operational sequence"
  policy: "Institutional organizational directive"
  metric: "Quantitative performance indicator"
  concept: "Definition or theoretical model"
```

### **Ontological Relationships**
```yaml
# --- Illustrative Examples ---
relationship_types:
  depends_on:
    description: "Semantically depends on another UKI"
    usage: "Structural dependencies, prerequisites"
    validation: "Target UKI must exist and be active"
    
  overrides:
    description: "Replaces or nullifies content of another UKI"
    usage: "Direct replacements, deprecation patterns"
    validation: "Target UKI should be marked as deprecated"
    
  conflicts_with:
    description: "Intentionally contradicts another UKI"
    usage: "Intentional incompatibilities, alternative approaches"
    validation: "Both UKIs cannot be active simultaneously in same scope"
    
  complements:
    description: "Expands or details another UKI"
    usage: "Collaborative extensions, additional details"
    validation: "Target UKI must be compatible and active"
    
  amends:
    description: "Corrects or partially updates"
    usage: "Corrections, incremental improvements"
    validation: "Target UKI version must be tracked"
    
  precedes:
    description: "Establishes order or priority"
    usage: "Sequences, implementation order"
    validation: "Circular dependencies must be prevented"
    
  equivalent_to:
    description: "Represents semantic equivalence"
    usage: "Equivalences, alternative representations"
    validation: "Semantic consistency must be maintained"

relationship_usage_examples:
  technical_dependency:
    source: "uki:technical:pattern:jwt-authentication"
    target: "uki:technical:constraint:security-requirements"
    type: "depends_on"
    description: "JWT implementation must follow security requirements"
    
  policy_override:
    source: "uki:business:policy:remote-work-2024"
    target: "uki:business:policy:office-mandatory-2019"
    type: "overrides"
    description: "New remote work policy replaces office-mandatory policy"
    
  architectural_conflict:
    source: "uki:technical:pattern:microservices-architecture"
    target: "uki:technical:pattern:monolithic-architecture"
    type: "conflicts_with"
    description: "Cannot implement both patterns simultaneously"
```

### **Severity Levels**
```yaml
# --- Illustrative Examples ---
severity_classification:
  low:
    description: "Minor impact, informational or enhancement suggestions"
    business_impact: "Minimal disruption to operations"
    technical_impact: "Non-critical system changes"
    examples:
      - "Documentation improvements"
      - "UI/UX enhancements"
      - "Performance optimizations"
    
  medium:
    description: "Moderate impact, affects specific functionality or processes"
    business_impact: "Localized impact on specific workflows"
    technical_impact: "Non-critical API changes"
    examples:
      - "Feature modifications"
      - "Process workflow updates"
      - "Integration adjustments"
    
  high:
    description: "Significant impact, affects core functionality or operations"
    business_impact: "Substantial impact on business operations"
    technical_impact: "Critical system functionality changes"
    examples:
      - "Core API modifications"
      - "Database schema changes"
      - "Security model updates"
    
  critical:
    description: "Critical impact, system failure or major disruption"
    business_impact: "Severe disruption to business operations"
    technical_impact: "System failure or major architecture changes"
    examples:
      - "Breaking API changes"
      - "Security vulnerabilities"
      - "Data migration requirements"

impact_assessment_matrix:
  technical_factors:
    - "API compatibility"
    - "Database schema impact"
    - "Integration dependencies"
    - "Performance implications"
    
  business_factors:
    - "User experience impact"
    - "Operational workflow changes"
    - "Compliance requirements"
    - "Revenue implications"
```

### **Lifecycle Management**
```yaml
# --- Illustrative Examples ---
lifecycle_states:
  active:
    description: "UKI active and in normal use"
    usage: "Current and valid knowledge"
    allowed_operations:
      - "can be referenced by other UKIs"
      - "can be updated with version control"
      - "visible in search and discovery"
    
  deprecated:
    description: "UKI discontinued but still referenced"
    usage: "Obsolete knowledge, avoid use"
    allowed_operations:
      - "read-only access for existing references"
      - "replacement UKI should be identified"
      - "migration path should be provided"
    
  archived:
    description: "UKI archived for historical reference"
    usage: "Historical preservation, do not use"
    allowed_operations:
      - "read-only historical access"
      - "cannot be referenced in new UKIs"
      - "metadata preserved for auditing"

lifecycle_transition_rules:
  active_to_deprecated:
    trigger: "Better alternative available or requirements changed"
    requirements:
      - "Replacement UKI must be identified"
      - "Migration plan must be documented"
      - "Dependent UKIs must be notified"
    
  deprecated_to_archived:
    trigger: "No active references remain"
    requirements:
      - "All dependent UKIs updated or archived"
      - "Historical value assessment completed"
      - "Archival metadata preserved"
    
  any_to_active:
    trigger: "Knowledge becomes relevant again"
    requirements:
      - "Content review and validation required"
      - "Version increment necessary"
      - "Stakeholder approval needed"
```

### **Organizational Customization Guide**
```yaml
# --- Implementation Guide ---
customization_methodology:
  step_1_domain_analysis:
    actions:
      - "Analyze your organization's knowledge domains"
      - "Identify unique knowledge types in your context"
      - "Map important relationships for your business"
    deliverables:
      - "Domain taxonomy specific to organization"
      - "Knowledge type classification system"
      - "Relationship mapping for business context"
    
  step_2_moc_configuration:
    actions:
      - "Define hierarchies in organizational MOC"
      - "Establish specific governance rules"
      - "Configure appropriate evaluation criteria"
    deliverables:
      - "Organizational MOC specification"
      - "Governance policy documentation"
      - "Validation rule configuration"
    
  step_3_implementation:
    actions:
      - "Configure automated validation based on MOC"
      - "Establish vocabulary evolution process"
      - "Implement consistency monitoring"
    deliverables:
      - "Automated validation system"
      - "Change management process"
      - "Quality monitoring dashboard"

industry_specific_examples:
  fintech_organization:
    domains: ["payments", "lending", "compliance", "fraud_detection", "customer_onboarding"]
    types: ["regulation", "risk_assessment", "financial_product", "security_control"]
    special_relationships: ["regulatory_compliance", "risk_mitigation"]
    
  healthcare_organization:
    domains: ["clinical", "regulatory", "patient_privacy", "care_quality", "interoperability"]
    types: ["clinical_guideline", "regulatory_requirement", "patient_protocol", "quality_metric"]
    special_relationships: ["clinical_evidence", "regulatory_mandate"]
    
  manufacturing_organization:
    domains: ["production", "quality_control", "supply_chain", "safety", "efficiency"]
    types: ["standard_procedure", "quality_standard", "safety_protocol", "efficiency_metric"]
    special_relationships: ["quality_dependency", "safety_requirement"]
```

---

## 8. Cross-References

- [Matrix Protocol — Main Specification](MATRIX_PROTOCOL.md)  
- [Matrix Protocol Integration Diagram](MATRIX_PROTOCOL_INTEGRATION_DIAGRAM.md)  
- [Matrix Protocol Glossary](MATRIX_PROTOCOL_GLOSSARY.md)  
- [Matrix Protocol Integration Diagram — Portuguese](MATRIX_PROTOCOL_INTEGRATION_DIAGRAM_PT.md)  
- [Matrix Protocol Glossary — Portuguese](MATRIX_PROTOCOL_GLOSSARY_PT.md)  
- [MEF — Matrix Embedding Framework](MEF_MATRIX_EMBEDDING_FRAMEWORK.md)  
- [MOC — Matrix Ontology Catalog](MOC_MATRIX_ONTOLOGY_CATALOG.md)  
- [ZOF — Zion Orchestration Framework](ZOF_ZION_ORCHESTRATION_FRAMEWORK.md)  
- [OIF — Operator Intelligence Framework](OIF_OPERATOR_INTELLIGENCE_FRAMEWORK.md)  