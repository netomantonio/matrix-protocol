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
1. **Oracle Layer**: Strategic governance & knowledge base management
2. **Zion Layer**: Integration between strategy and operations, intelligent agents
3. **Operator Layer**: Practical execution and implementation by development teams

### MEF (Matrix Embedding Framework)
- Standardized YAML format for knowledge units (UKIs)
- Structured with domains: `product`, `business`, `technical`, `strategy`, `culture`
- Types: `business_rule`, `function`, `template`, `guideline`, `pattern`, `decision`, `example`
- Contexts: `discovery`, `implementation`, `refinement`, `qa`, `documentation`, `support`

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
id: unik-[domain]-[identifier]
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
  - unik-[other-related-units]
last_validation: [YYYY-MM-DD]
```

### Knowledge Organization
- Organize by domain directories (`technical/`, `business/`, `product/`, etc.)
- Use semantic IDs following `unik-domain-identifier` pattern
- Implement semantic versioning for knowledge evolution tracking
- Maintain bidirectional relationships between related concepts
- Regular validation of content freshness and accuracy
- Document change impact and maintain version history

## Working with Examples

The `examples/` directory contains comprehensive UKI demonstrations:

### Practical Examples Available
- **Technical**: JWT authentication patterns with security considerations
- **Business**: Customer discount rules with calculation formulas
- **Product**: Modal design guidelines with accessibility standards
- **Strategy**: API evolution strategies with migration timelines
- **Culture**: Code review processes with collaboration principles

### Using Examples
- Reference templates for creating new UKIs
- Study MEF field usage patterns
- Understand versioning implementation
- Learn bilingual documentation approaches
- Validate MEF parser implementations

## AI Integration Considerations

This framework is designed for:
- Semantic search and knowledge discovery
- Context-aware AI assistance with versioned knowledge
- Automated knowledge validation and evolution tracking
- Cross-domain relationship mapping
- Knowledge graph construction with temporal awareness
- Version-aware knowledge recommendations

The MEF format enables AI systems to understand not just the content but also the intent, context, evolution history, and relationships of knowledge units for more intelligent assistance.