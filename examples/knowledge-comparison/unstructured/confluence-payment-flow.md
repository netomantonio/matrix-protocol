# Fluxo de Pagamentos - Wiki Squad

*Última atualização: março 2022*  
*Autor: Pedro Silva (não está mais na empresa)*  

## Visão Geral

Este documento descreve o fluxo completo de pagamentos da plataforma.

**⚠️ ATENÇÃO: Este documento pode estar desatualizado**

## Gateways Disponíveis

1. **PagSeguro** (principal até nov/2022)
2. **Mercado Pago** (backup)
3. **Stripe** (piloto - apenas produtos digitais)

### Configurações Gateway

```
PagSeguro:
- Endpoint: https://ws.pagseguro.uol.com.br/v2/
- Timeout: 30s
- Retry: 3x
- Sandbox: https://ws.sandbox.pagseguro.uol.com.br/v2/

Mercado Pago:
- [Link quebrado para documentação]
```

## Fluxo de Checkout

1. Cliente seleciona produtos
2. Sistema calcula frete (integração Correios)
3. Aplicação desconto (se houver)
4. Redirect para gateway
5. Processamento pagamento
6. Webhook confirmação
7. Atualização pedido

![Diagrama Fluxo](./images/payment-flow-2022.png) *(imagem não encontrada)*

## Regras de Desconto

### Desconto por Volume
- Compras > R$ 500: 5% desconto  
- Compras > R$ 1000: 10% desconto
- Compras > R$ 2000: 15% desconto (máximo)

### Cupons
- Cupom PRIMEIRA: 20% primeira compra
- Cupom VOLTA: 10% cliente recorrente  
- Cupom AMIGO: 5% indicação amigo

**Importante:** Cupons não acumulam com desconto por volume

## Detecção Fraude

Sistema básico implementado:
- IP geolocalização (bloquear países de risco)
- Validação CPF (integração Receita Federal - **API descontinuada**)
- Análise comportamental (mais de 5 tentativas = suspeito)

### Países Bloqueados
- Nigéria
- Venezuela  
- Rússia (adicionado em fev/2022 devido ao conflito)

## Monitoramento

Dashboard disponível em: http://internal-dash.company.com/payments *(link não funciona mais)*

Métricas importantes:
- Taxa conversão checkout
- Tempo resposta gateways
- Volume transações por hora
- Chargebacks mensais

## Contatos Importantes

- Suporte PagSeguro: suporte@pagseguro.com (email antigo)
- Gerente conta MP: jose.silva@mercadopago.com (pessoa saiu da empresa)
- Time Fraude: fraud@company.com *(email não existe mais)*

## TODOs (nunca foram feitos)

- [ ] Implementar retry inteligente por gateway
- [ ] Melhorar logs de auditoria  
- [ ] Criar alertas automáticos para SLA
- [ ] Documentar processo de reconciliação
- [ ] Atualizar SDK do PagSeguro (versão 2018!)

---
*Este documento é mantido pela Squad Pagamentos. Em caso de dúvidas, entre em contato.*