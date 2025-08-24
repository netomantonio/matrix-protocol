# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains the **Matrix Protocol** specification - a comprehensive framework for human-AI collaboration through three interdependent layers: Oracle (strategic governance), Zion (integration), and Operator (execution).

The project includes the **Matrix Embedding Framework (MEF)** - a standardized knowledge structuring protocol that defines how to create, store, and utilize Units of Knowledge Interlinked (UKIs) for AI consumption.

## Repository Structure

This repository contains comprehensive Matrix Protocol documentation and examples:

- `MATRIX_PROTOCOL.md` - Complete Matrix Protocol specification (Portuguese/English)
- `MEF_MATRIX_EMBEDDING_FRAMEWORK.md` - MEF technical specification and implementation guide
- `examples/` - Practical UKI examples demonstrating MEF implementation across all domains
  - Technical domain examples (JWT authentication patterns)
  - Business domain examples (discount calculation rules)
  - Product domain examples (modal design guidelines)
  - Strategy domain examples (API evolution strategies)
  - Culture domain examples (code review processes)
  - Bilingual examples (Portuguese and English)

## Core Concepts

### Matrix Protocol Layers
1. **Oracle Layer**: Strategic governance & knowledge base management (MEF)
2. **Zion Layer**: Conceptual workflow framework for AI-oriented teams (ZWF)
3. **Operator Layer**: Practical execution and implementation by development teams

### MEF (Matrix Embedding Framework)
- Standardized YAML format for knowledge units (UKIs)
- Structured with domains: `product`, `business`, `technical`, `strategy`, `culture`
- Types: `business_rule`, `function`, `template`, `guideline`, `pattern`, `decision`, `example`
- Contexts: `discovery`, `implementation`, `refinement`, `qa`, `documentation`, `support`

### ZWF (Zion Workflow Framework)
- Conceptual framework for AI-oriented workflows as state machines
- Canonical states: `Intake → Understand → Decide → Act → Review → Enrich`
- Events: `knowledge.added`, `work.proposed`, `work.refine.requested`, `assistance.requested`, `test.authored`, `feedback.submitted`
- Technology-independent: defines "how to think" not "how to implement"
- Always enriches Oracle with MEF UKIs at the end

## Working with This Repository

### Content Guidelines
- All specifications are bilingual (Portuguese/English)
- Follow MEF format when creating new knowledge units
- Maintain semantic relationships between concepts
- Use Mermaid diagrams for visual representations in documentation

### Documentation Standards
- Use structured YAML for formal knowledge specifications
- Include practical examples with input/output pairs
- Maintain version control for specification changes
- Document semantic relationships between concepts

## MEF Implementation

When working with MEF specifications:

### UKI Structure Example
```yaml
id: uki-[domain]-[identifier]
title: [Descriptive title]
domain: [product|business|technical|strategy|culture]
type: [business_rule|function|template|guideline|pattern|decision|example]
context: [discovery|implementation|refinement|qa|documentation|support]
version: [MAJOR.MINOR.PATCH]  # Semantic versioning
created_date: [YYYY-MM-DD]  # Creation date
last_modified: [YYYY-MM-DD]  # Last modification
change_summary: [Summary of changes]  # For versions > 1.0.0
change_impact: [major|minor|patch]  # Impact classification
previous_version: [MAJOR.MINOR.PATCH]  # Previous version reference
content: |
  [Main content with clear structure]
examples:
  - input: [Real scenario]
    output: [Expected result]
related_to:
  - target: uki-[target-uki-id]
    relation_type: [implements|depends_on|extends|replaces|complies_with|conflicts_with|derives_from|relates_to]
    description: [Specific description of the relationship]
last_validation: [YYYY-MM-DD]
```

### Knowledge Organization
- Organize by domain directories (`technical/`, `business/`, `product/`, etc.)
- Use semantic IDs following `uki:[domain_ref]:[type_ref]:[slug_or_id]` pattern
- Implement semantic versioning for knowledge evolution tracking
- Maintain bidirectional relationships between related concepts using typed semantic relationships
- Regular validation of content freshness and accuracy
- Document change impact and maintain version history

## Working with Examples

The `examples/` directory contains comprehensive demonstrations:

### Oracle MEF Examples (`examples/oracle-mef/`)
- **Technical**: JWT authentication patterns with security considerations
- **Business**: Customer discount rules with calculation formulas
- **Product**: Modal design guidelines with accessibility standards
- **Strategy**: API evolution strategies with migration timelines
- **Culture**: Code review processes with collaboration principles
- **Format**: Separate PT/EN files (e.g., `uki:technical:pattern:auth-pt.yaml`, `uki:technical:pattern:auth-en.yaml`)

### Zion ZWF Examples (`examples/zion-workflows/`)
- **Request Flow**: Technical implementation following canonical states
- **Refinement Flow**: Product optimization with incremental approach
- **Ingestion Flow**: Knowledge processing from external sources
- **Format**: Separate PT/EN files (e.g., `zwf-jwt-implementation-pt.yaml`, `zwf-jwt-implementation-en.yaml`)

### Using Examples
- Reference templates for creating new UKIs and ZWF flows
- Study MEF field usage patterns and ZWF state transitions
- Understand versioning implementation and flow traceability
- Learn bilingual documentation approaches
- Validate MEF parser implementations and ZWF compliance

## AI Integration Considerations

This framework is designed for:
- Semantic search and knowledge discovery
- Context-aware AI assistance with versioned knowledge
- Automated knowledge validation and evolution tracking
- Cross-domain relationship mapping
- Knowledge graph construction with temporal awareness
- Version-aware knowledge recommendations

The MEF format enables AI systems to understand not just the content but also the intent, context, evolution history, and relationships of knowledge units for more intelligent assistance.

## ZWF Implementation

When working with ZWF workflow specifications:

### ZWF Flow Structure Example
```yaml
flow_id: zwf-[workflow-type]-[identifier]
flow_name: "[Descriptive workflow name in PT/EN]"
triggered_by: [knowledge.added|work.proposed|work.refine.requested|assistance.requested|test.authored|feedback.submitted]
trigger_context: "[Context description in PT/EN]"
team_context: "[Team/squad information]"

oracle_context:
  motivating_ukis:
    - uki-[domain]-[related-knowledge]

flow_execution:
  - state: "intake"
    signals:
      context: "[What came in / O que entrou]"
      decision: "[Why it transitioned / Por que transicionou]" 
      result: "[What came out / O que saiu]"
```

### ZWF Guidelines
- All flows must follow canonical states: Intake → Understand → Decide → Act → Review → Enrich
- Always consult Oracle UKIs to justify decisions
- Record explainability signals (context, decision, result) at each state
- Must enrich Oracle with MEF UKIs at the end
- Technology-independent: focus on "how to think" not "how to implement"
- Separate PT/EN files for bilingual support