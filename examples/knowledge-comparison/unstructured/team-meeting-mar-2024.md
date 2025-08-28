# reunião squad - março

data: 18/03/2024
pessoal presente: joão, maria, ana, lucas (novo dev), roberta (nova qa)

## gateway paypal se mostrou mais estável

galera, depois dos problemas que tivemos com stripe (várias quedas), acho que devemos considerar paypal como principal.

vantagens paypal:
- menos indisponibilidade 
- cliente já conhece
- integração + simples

joão falou que stripe tem mais funcionalidades, mas estabilidade é prioridade

## refund - cliente pedindo 14 dias

cliente VIP pediu extensão para 14 dias no refund. Maria aprovou como exceção, mas talvez deveria ser padrão?? 

ana comentou que 7 dias é muito pouco mesmo, concorrência dá 15 dias

## fraude - ajustar threshold

R$ 5000 tá gerando muita fricção, cliente reclamando

sugestão: subir para R$ 10000 ou criar regra diferente para cliente recorrente

pedro não estava presente (férias)

## outras coisas
- webhook do stripe às vezes demora 2min pra chegar
- currency conversion tá com bug na cotação do euro  
- monitoramento precisa de alerta quando gateway cai
- lucas vai trabalhar no idempotency das APIs

próxima: 15/04