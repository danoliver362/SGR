# Casos de Uso

## UC-001 — Atendimento rápido

### Objetivo
Registrar um atendimento que pode ser realizado e concluído no momento em que o cliente está na loja.

### Ator principal
Atendente

### Pré-condições
- O cliente está presente na loja.
- O serviço pode ser realizado imediatamente.

### Fluxo principal
1. O atendente identifica o cliente.
2. O atendente registra o cliente no sistema, caso ainda não esteja cadastrado.
3. O atendente adiciona um ou mais relógios ao atendimento.
4. O atendente registra o serviço solicitado para cada relógio.
5. O serviço é realizado.
6. O atendente registra o valor de cada serviço.
7. O sistema apresenta o valor total do atendimento.
8. O atendente registra a forma de pagamento.
9. O atendimento é concluído.

### Resultado
O atendimento fica registrado no histórico do cliente como concluído.

## UC-002 — Serviço com orçamento

### Objetivo
Registrar e acompanhar um serviço que necessita de orçamento antes de sua realização.

### Ator principal
Atendente

### Pré-condições

O cliente deixou o relógio para avaliação.
O serviço não pode ser realizado sem definição prévia do orçamento.

### Fluxo principal

### Fluxo principal

1. O atendente registra o resultado da avaliação.
2. O atendente identifica a necessidade de orçamento.
3. O atendente verifica a peça necessária e seu valor, quando aplicável.
4. O atendente registra o valor do orçamento quando as informações estiverem disponíveis.
5. O atendente entra em contato com o cliente.
6. O cliente recebe as informações sobre o serviço e o valor.
7. O atendente registra a aprovação ou recusa do orçamento.
8. Em caso de aprovação, o serviço pode prosseguir.
   
### Fluxo alternativo — Valor ainda não disponível

1. O cliente entra em contato antes da definição do orçamento.
2. O atendente informa que o valor ainda está sendo verificado.
3. O atendimento permanece pendente.
4. Quando o valor estiver disponível, o cliente é contatado novamente.
