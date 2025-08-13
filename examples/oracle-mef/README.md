# MEF Examples | Exemplos MEF

This directory contains practical examples of UKIs (Units of Knowledge Interlinked) following the Matrix Embedding Framework specification.

Este diretório contém exemplos práticos de UKIs (Units of Knowledge Interlinked) seguindo a especificação do Matrix Embedding Framework.

## 📁 Structure | Estrutura

The examples are organized by domain and language:
Os exemplos estão organizados por domínio e idioma:

### 🔧 Technical Domain | Domínio Técnico
- `unik-technical-authentication-pattern-pt.yaml` - JWT authentication pattern (Portuguese)
- `unik-technical-authentication-pattern-en.yaml` - JWT authentication pattern (English)

### 💼 Business Domain | Domínio de Negócio
- `unik-business-discount-rule-pt.yaml` - Customer loyalty discount rule (Portuguese)
- `unik-business-discount-rule-en.yaml` - Customer loyalty discount rule (English)

### 🎨 Product Domain | Domínio de Produto
- `unik-product-modal-guideline-pt.yaml` - Modal design guidelines (Portuguese)
- `unik-product-modal-guideline-en.yaml` - Modal design guidelines (English)

### 🎯 Strategy Domain | Domínio de Estratégia
- `unik-strategy-api-evolution-pt.yaml` - API evolution strategy (Portuguese)
- `unik-strategy-api-evolution-en.yaml` - API evolution strategy (English)

### 🤝 Culture Domain | Domínio de Cultura
- `unik-culture-code-review-pt.yaml` - Code review process (Portuguese)
- `unik-culture-code-review-en.yaml` - Code review process (English)

## 🎯 Purpose | Propósito

These examples demonstrate:
Estes exemplos demonstram:

- **Complete MEF Structure**: All required and optional fields properly filled
- **Bilingual Support**: Same concepts in Portuguese and English
- **Domain Variety**: Examples across all MEF domains
- **Typed Semantic Relationships**: Demonstrates the new typed relationship format
- **Active Governance**: Implementation of automatic propagation and impact control
- **Best Practices**: Proper use of versioning, examples, and semantic connections
- **Real-world Scenarios**: Practical situations teams face daily

- **Estrutura MEF Completa**: Todos os campos obrigatórios e opcionais preenchidos adequadamente
- **Suporte Bilíngue**: Mesmos conceitos em português e inglês
- **Variedade de Domínios**: Exemplos em todos os domínios MEF
- **Relacionamentos Semânticos Tipados**: Demonstra o novo formato de relacionamentos tipados
- **Governança Ativa**: Implementação de propagação automática e controle de impacto
- **Melhores Práticas**: Uso adequado de versionamento, exemplos e conexões semânticas
- **Cenários Reais**: Situações práticas que equipes enfrentam diariamente

## 🚀 Usage | Uso

Use these examples as:
Use estes exemplos como:

1. **Templates**: Starting point for your own UKIs
2. **Learning Material**: Understanding MEF concepts
3. **Validation**: Testing MEF implementations
4. **Training**: Onboarding team members to MEF

1. **Templates**: Ponto de partida para suas próprias UKIs
2. **Material de Aprendizado**: Compreensão dos conceitos MEF
3. **Validação**: Teste de implementações MEF
4. **Treinamento**: Integração de membros da equipe ao MEF

## 🔗 Typed Semantic Relationships | Relacionamentos Semânticos Tipados

All examples demonstrate the new typed relationship format:
Todos os exemplos demonstram o novo formato de relacionamentos tipados:

```yaml
related_to:
  - target: unik-target-id
    relation_type: implements|depends_on|extends|replaces|complies_with|conflicts_with|derives_from|relates_to
    description: Clear description of the relationship
```

### Relationship Types Used | Tipos de Relacionamento Utilizados

- **`implements`**: Implements patterns, guidelines, or rules | Implementa padrões, diretrizes ou regras
- **`complies_with`**: Follows policies or standards | Segue políticas ou padrões  
- **`depends_on`**: Requires other knowledge to function | Requer outro conhecimento para funcionar
- **`extends`**: Extends or enhances existing concepts | Estende ou aprimora conceitos existentes
- **`relates_to`**: General contextual relationship | Relacionamento contextual geral

## 🎛️ Active Governance Examples | Exemplos de Governança Ativa

All examples now include the new `governance` field that enables automatic change propagation and impact analysis:
Todos os exemplos agora incluem o novo campo `governance` que habilita propagação automática de mudanças e análise de impacto:

```yaml
governance:
  criticality: [critical | high | medium | low]
  auto_propagation: [automatic | semi_automatic | manual]
  validation_frequency: [30 | 60 | 90]  # days
  impact_analysis:
    structural_changes: [breaking | compatible | additive]
    dependent_ukis: [number]
    propagation_scope: [immediate | scheduled | informative]
  propagation_rules:
    on_major_change: [notify_all | validate_dependencies | manual_review]
    on_minor_change: [suggest_updates | validate_compatibility | auto_notify]
    on_patch_change: [auto_propagate | inform_dependents | track_only]
```

### Governance Configurations by Domain | Configurações de Governança por Domínio

| Domain | Criticality | Auto Propagation | Validation Frequency |
|--------|-------------|------------------|---------------------|
| **Technical** | Critical | Semi-automatic | 30 days |
| **Business** | High | Semi-automatic | 60 days |
| **Strategy** | High | Manual | 60 days |
| **Product** | Medium | Manual | 90 days |
| **Culture** | Medium | Manual | 90 days |

| Domínio | Criticidade | Propagação Automática | Frequência de Validação |
|---------|-------------|----------------------|------------------------|
| **Technical** | Crítica | Semi-automática | 30 dias |
| **Business** | Alta | Semi-automática | 60 dias |
| **Strategy** | Alta | Manual | 60 dias |
| **Product** | Média | Manual | 90 dias |
| **Culture** | Média | Manual | 90 dias |

### Impact Analysis Examples | Exemplos de Análise de Impacto

- **Breaking Changes**: Technical authentication patterns (8 dependent UKIs)
- **Compatible Changes**: Business discount rules (5 dependent UKIs) 
- **Additive Changes**: Product design guidelines (3 dependent UKIs)

- **Mudanças Críticas**: Padrões de autenticação técnica (8 UKIs dependentes)
- **Mudanças Compatíveis**: Regras de desconto de negócio (5 UKIs dependentes)
- **Mudanças Aditivas**: Diretrizes de design de produto (3 UKIs dependentes)

## 🔗 Related Documentation | Documentação Relacionada

- [MEF Specification](../MEF_MATRIX_EMBEDDING_FRAMEWORK.md)
- [Matrix Protocol](../MATRIX_PROTOCOL.md)
- [Claude.md](../CLAUDE.md)

---

**Matrix Protocol v1.0** | **Protocolo Matrix v1.0**