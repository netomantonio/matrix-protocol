# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains the **Matrix Protocol** specification - a comprehensive framework for human-AI collaboration through three interdependent layers: Oracle (strategic governance), Zion (integration), and Operator (execution).

The project includes the **Matrix Embedding Framework (MEF)** - a standardized knowledge structuring protocol that defines how to create, store, and utilize Units of Knowledge Interlinked (UKIs) for AI consumption.

## Repository Structure

This is a documentation-only repository containing:

- `MATRIX_PROTOCOL.md` - Complete Matrix Protocol specification (Portuguese/English)
- `MEF_MATRIX_EMBEDDING_FRAMEWORK.md` - MEF technical specification and implementation guide

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
- Maintain bidirectional relationships between related concepts
- Regular validation of content freshness and accuracy

## AI Integration Considerations

This framework is designed for:
- Semantic search and knowledge discovery
- Context-aware AI assistance
- Automated knowledge validation
- Cross-domain relationship mapping
- Knowledge graph construction

The MEF format enables AI systems to understand not just the content but also the intent, context, and relationships of knowledge units for more intelligent assistance.