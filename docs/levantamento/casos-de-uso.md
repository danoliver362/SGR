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

## UC-003 — Serviço aguardando peça

### Objetivo

Registrar e acompanhar um serviço que depende da disponibilidade de uma peça para ser realizado.

### Ator principal

Atendente

### Pré-condições

- O relógio foi recebido para serviço.
- A avaliação identificou a necessidade de uma peça.

### Fluxo principal

1. O atendente registra a necessidade da peça.
2. O atendente verifica a disponibilidade da peça.
3. Caso a peça esteja disponível, o serviço pode prosseguir.
4. Caso a peça não esteja disponível, o atendente registra a necessidade de encomenda.
5. O atendente registra o prazo estimado para obtenção da peça.
6. O atendimento permanece pendente enquanto a peça não estiver disponível.
7. Quando a peça estiver disponível, o atendimento pode prosseguir.
8. O serviço é realizado.

### Fluxo alternativo — Prazo maior

1. A peça precisa ser encomendada.
2. O prazo inicialmente informado pode ser alterado.
3. O cliente é informado sobre a necessidade de aguardar a peça e sobre o novo prazo.
4. O atendimento permanece pendente até a disponibilidade da peça.

## UC-004 — Alteração de prazo

### Objetivo

Registrar e acompanhar a alteração do prazo estimado para conclusão de um serviço.

### Ator principal

Atendente

### Pré-condições

- O serviço está em andamento.
- Existe um prazo estimado para sua conclusão.

### Fluxo principal

1. O atendente identifica que o prazo inicialmente estimado não poderá ser cumprido.
2. O atendente registra o novo prazo estimado.
3. O atendente registra o motivo da alteração, quando necessário.
4. O cliente é informado sobre a alteração do prazo.
5. O serviço permanece em acompanhamento até sua conclusão.

### Resultado

O novo prazo fica registrado no atendimento e o cliente é informado sobre a alteração.

## UC-005 — Serviço concluído e aguardando retirada

### Objetivo

Registrar a conclusão do serviço e acompanhar o relógio até sua retirada pelo cliente.

### Ator principal

Atendente

### Pré-condições

- O serviço foi concluído.
- O relógio está disponível para retirada.

### Fluxo principal

1. O atendente registra a conclusão do serviço.
2. O atendente identifica o telefone do cliente na etiqueta do relógio.
3. O atendente entra em contato com o cliente para informar que o relógio está pronto.
4. O relógio é colocado no gancho de prontos para retirada.
5. O atendimento permanece aguardando a retirada do cliente.
6. O cliente comparece à loja para retirar o relógio.
7. O atendente localiza o atendimento no sistema.
8. O atendente registra a retirada do relógio.
9. O atendente registra a data de retirada.
10. O atendente registra a garantia aplicável ao serviço, quando houver.

### Fluxo alternativo — Cliente sem o cartão

1. O cliente comparece à loja sem o cartão.
2. O atendente localiza o atendimento utilizando as informações disponíveis.
3. O cliente é orientado a trazer o cartão posteriormente para que a baixa seja realizada.

### Fluxo alternativo — Cartão perdido

1. O cliente informa que perdeu o cartão.
2. O atendente registra a retirada em um caderno utilizado pela loja.
3. São registrados o modelo do relógio, o serviço realizado e a assinatura do cliente.
4. A retirada é considerada registrada conforme o procedimento adotado pela loja.

### Resultado

A retirada do relógio fica registrada, juntamente com a data e as informações de garantia, quando aplicável.

## UC-006 — Retirada parcial

### Objetivo

Registrar a retirada de um ou mais relógios de um atendimento que ainda possui outros relógios pendentes.

### Ator principal

Atendente

### Pré-condições

- O atendimento possui dois ou mais relógios.
- Pelo menos um dos relógios está pronto para retirada.
- Existem outros relógios que ainda permanecem pendentes ou em andamento.

### Fluxo principal

1. O cliente comparece à loja para retirar um ou mais relógios.
2. O atendente localiza o atendimento no sistema.
3. O sistema apresenta os relógios associados ao atendimento e seus respectivos status.
4. O atendente identifica quais relógios serão retirados.
5. O atendente registra a retirada dos relógios selecionados.
6. O atendente registra a data de retirada.
7. O sistema mantém os demais relógios no atendimento com seus respectivos status.
8. O atendimento permanece aberto enquanto existirem relógios pendentes.

### Resultado

Os relógios retirados ficam registrados como retirados, enquanto os demais continuam sendo acompanhados no mesmo atendimento.
