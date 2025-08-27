# Ata de Reunião da Squad Pagamentos - Janeiro 2024

**Data:** 15/01/2024  
**Participantes:** João (Tech Lead), Maria (PO), Pedro (Dev Senior), Ana (QA), Carlos (DevOps)  
**Duração:** 1h30min  

## Decisões Tomadas

### Gateway de Pagamento Principal
Após análise das opções disponíveis, decidimos adotar **Stripe** como gateway principal pelos seguintes motivos:
- API mais robusta
- Documentação melhor
- Suporte a mais países
- Taxas competitivas

**Responsável:** Pedro  
**Prazo:** Final de fevereiro  

### Política de Refund
- Refunds processados em **até 7 dias úteis**
- Valores acima de R$ 1000 precisam de aprovação manual
- Refund parcial permitido apenas uma vez por pedido

### Detecção de Fraude
Implementar regras básicas:
- Transações acima de R$ 5000 → revisão manual
- Mais de 3 cartões diferentes no mesmo IP em 1 hora → bloquear
- CVV inválido 2x seguidas → sinalizar como suspeito

## Pendências
- [ ] Definir fluxo para chargebacks
- [ ] Revisar configurações do PCI compliance
- [ ] Criar dashboard de monitoramento

## Próxima reunião
Data: 12/02/2024  
Pauta: Review da implementação Stripe