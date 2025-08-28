# 5 Exemplos Transformados: Antes vs. Depois
**Demonstração Prática de Estruturação de Conhecimento**

---

## 📋 **Exemplo 1: Política de Refund**

### ❌ **ANTES** (Informação Dispersa)
```
Thread Slack:
[10:23] maria: cliente quer refund, 7 dias úteis né?
[10:25] joão: acho que é 7 dias sim
[2 semanas depois...]
[14:12] maria: cliente VIP pode ter 14 dias?
[14:13] joão: pode, mas vamos revisar política
```

### ✅ **DEPOIS** (Estruturado)
```yaml
título: "Política de Refund - Padrões e Prazos"
categoria: "Regra de Negócio"
criado_em: "2024-03-25"
atualizado_em: "2024-03-25"
status: "Ativo"
responsável: "Squad Pagamentos"

regras_principais:
  - prazo_padrão: "14 dias corridos da compra"
  - prazo_vip: "30 dias corridos (programa fidelidade)"
  - aprovação_manual: "Valores acima R$ 1.000"

exemplos:
  - situação: "Cliente comum, compra R$ 800, solicita após 10 dias"
    resultado: "Aprovado automaticamente, processamento 3-5 dias"
  
  - situação: "Cliente VIP, compra R$ 1.200, solicita após 20 dias"
    resultado: "Aprovado (dentro prazo VIP), aprovação manual obrigatória"

relacionado_com:
  - "Cálculo de Taxas por Gateway"
  - "Processo de Atendimento ao Cliente"
```

---

## 📋 **Exemplo 2: Detecção de Fraude**

### ❌ **ANTES** (Ticket JIRA Confuso)
```
Tivemos aumento de 23% em chargebacks. Casos específicos:
1. Mesmo IP, 15 compras, cartões diferentes, Friday night
2. Threshold R$ 5000 não funcionou? (BUG?)
3. CVV 000 passou (Ana já sabe)

João comentou: "Threshold talvez alto. Vamos para R$ 3500"
Pedro: "CVV bug existe, vou corrigir essa semana"
```

### ✅ **DEPOIS** (Estruturado)
```yaml
título: "Regras de Detecção de Fraude - Thresholds Ativos"
categoria: "Regra de Negócio"
criado_em: "2024-03-25"
atualizado_em: "2024-03-25"
status: "Ativo"
responsável: "Squad Pagamentos + Risco"

regras_principais:
  - threshold_valor: "R$ 3.500 (reduzido de R$ 5.000)"
  - múltiplas_tentativas: "3+ cartões diferentes no mesmo IP em 1h = bloqueio"
  - cvv_inválidos: "Bloquear: 000, 111, 222, etc."
  - cliente_recorrente: "Threshold R$ 5.000 (histórico positivo)"

exemplos:
  - situação: "Transação R$ 4.000, cliente novo, dados consistentes"
    resultado: "Revisão manual obrigatória (acima threshold)"
  
  - situação: "3 cartões diferentes, mesmo IP, 30 minutos"
    resultado: "Bloqueio automático + alerta time risco"

notas_importantes:
  - "CVV validation corrigida em 2024-03-26"
  - "Alertas integrados ao Slack #fraude-alerts"
  - "Métricas monitoradas: taxa falsos positivos"

próxima_revisão: "2024-05-25"
```

---

## 📋 **Exemplo 3: Processo de Deploy**

### ❌ **ANTES** (Checklist Desatualizado)
```
ONBOARDING CHECKLIST - Abril 2022
Responsável: Pedro Silva (ex-funcionário)

Deploy produção:
- Só com aprovação João ou Pedro
- Deploy sexta-feira (PROIBIDO!)
- Ambiente QA: payments-qa.company.com (servidor desligado)
- New Relic (conta cancelada em 2023)
```

### ✅ **DEPOIS** (Estruturado)
```yaml
título: "Processo de Deploy - Sistema Pagamentos"
categoria: "Procedimento Técnico"
criado_em: "2024-03-25"
atualizado_em: "2024-03-25"
status: "Ativo"
responsável: "DevOps + Tech Lead"

regras_principais:
  - ambientes: "Development → QA → Staging → Production"
  - aprovação_prod: "Tech Lead + PO (aprovação dupla)"
  - janela_permitida: "Terça a Quinta, 10h-16h BRT"
  - janela_bloqueada: "Sextas, segundas, feriados"

exemplos:
  - situação: "Deploy normal, quarta-feira 14h"
    resultado: "Seguir pipeline completo, testes obrigatórios"
  
  - situação: "Hotfix crítico, sábado 20h"
    resultado: "Emergency deployment, CTO notification, testes mínimos"

exceções:
  - "Emergency: P0 incident, security fix, revenue impact > R$ 50K/dia"

relacionado_com:
  - "Procedimento Incident Response"
  - "Configuração Monitoramento"
  - "Checklist PCI Compliance"

próxima_revisão: "2024-06-25"
```

---

## 📋 **Exemplo 4: Integração Gateway**

### ❌ **ANTES** (Anotações Pessoais)
```
ANOTAÇÕES DIVERSAS - João (arquivo pessoal)

Gateway lento ultimamente:
- Stripe: média 8s (antes era 3s)
- PayPal: média 5s (OK)
- Timeout cliente: 15s (muito baixo?)

TECH DEBT:
- Circuit breaker (hystrix descontinuado, usar resilience4j)
- Timeout paypal muito alto (configurar 30s)
```

### ✅ **DEPOIS** (Estruturado)
```yaml
título: "Integração Gateway - Configurações e Timeouts"
categoria: "Padrão Técnico"
criado_em: "2024-03-25"
atualizado_em: "2024-03-25"
status: "Ativo"
responsável: "Squad Pagamentos"

configurações_atuais:
  - timeout_conexão: "5 segundos"
  - timeout_leitura: "30 segundos (reduzido de 90s)"
  - circuit_breaker: "50% falhas em 10 requests"
  - retry_policy: "3 tentativas com backoff exponencial"

exemplos:
  - situação: "Stripe timeout, circuit breaker fechado"
    resultado: "Retry com backoff, failover PayPal se 50% falhas"
  
  - situação: "PayPal retorna 503, circuito aberto"
    resultado: "Fail fast, não retry, usuário notificado"

métricas_monitoradas:
  - "Latência p95 por gateway"
  - "Taxa erro por endpoint"
  - "Frequência ativação circuit breaker"

alertas_configurados:
  - "Latência p95 > 10s → Slack #alerts"
  - "Circuit breaker OPEN → SMS plantão"

relacionado_com:
  - "Estratégia Retry Operations"
  - "Incident Response Payments"

próxima_revisão: "2024-04-25"
```

---

## 📋 **Exemplo 5: Cálculo de Descontos**

### ❌ **ANTES** (Ata de Reunião Informal)
```
# reunião squad - março
pessoal presente: joão, maria, ana, lucas

## gateway paypal se mostrou mais estável
vantagens paypal: menos indisponibilidade, cliente já conhece

## refund - cliente pedindo 14 dias
ana comentou que 7 dias é muito pouco mesmo

## fraude - ajustar threshold  
R$ 5000 tá gerando fricção, subir para R$ 10000?
```

### ✅ **DEPOIS** (Estruturado)
```yaml
título: "Regras de Desconto - Volume e Cupons"
categoria: "Regra de Negócio"
criado_em: "2024-03-25"
atualizado_em: "2024-03-25"
status: "Ativo"
responsável: "Squad Pagamentos + Produto"

regras_volume:
  - faixa_1: "R$ 500-999: 5% desconto"
  - faixa_2: "R$ 1.000-1.999: 10% desconto"
  - faixa_3: "R$ 2.000+: 15% desconto máximo"

cupons_ativos:
  - primeira_compra: "PRIMEIRA: 20% (máximo R$ 100)"
  - cliente_recorrente: "VOLTA: 10% (sem limite)"
  - indicação: "AMIGO: 5% (ambos recebem)"

precedência:
  - regra: "Cupom vs Volume → aplicar maior valor"
  - limitação: "Apenas 1 cupom por transação"

exemplos:
  - situação: "Carrinho R$ 1.200 + cupom PRIMEIRA"
    resultado: "Aplicar cupom R$ 100 (limitado), não volume R$ 120"
  
  - situação: "Carrinho R$ 2.500 + cupom AMIGO (5%)"
    resultado: "Aplicar volume R$ 375 (15% > 5% cupom)"

validações_obrigatórias:
  - "Cupom PRIMEIRA: verificar primeira compra CPF"
  - "Cupom VOLTA: mínimo 30 dias última compra"
  - "Valor mínimo R$ 50 para qualquer desconto"

relacionado_com:
  - "Cálculo Taxas Gateway"
  - "Política Refund Proporcional"

próxima_revisão: "2024-06-25"
```

---

## 📊 **Resumo do Impacto da Transformação**

| Aspecto | Antes | Depois |
|---------|-------|---------|
| **Clareza** | Informação dispersa, ambígua | Regras específicas, exemplos práticos |
| **Atualização** | Datas perdidas, status indefinido | Versionamento claro, dono definido |
| **Relacionamentos** | Isolado, sem contexto | Conectado com outros processos |
| **Aplicabilidade** | "Depende", genérico | Cenários específicos, ações claras |
| **Confiança** | "Acho que é assim" | Status validado, responsável definido |
| **IA Capability** | Respostas vagas, contradições | Respostas precisas, fontes citadas |

## 🎯 **Padrão Identificado**

**Transformação segue sempre:**
1. **Título vago** → **Título específico**
2. **Conteúdo disperso** → **Estrutura consistente**  
3. **Regras implícitas** → **Regras explícitas**
4. **Sem exemplos** → **Cenários práticos**
5. **Isolado** → **Conectado com outros conhecimentos**
6. **Sem dono** → **Responsabilidade clara**

**Resultado**: IA sai de "talvez" para "baseado em [fonte específica], a resposta é X"