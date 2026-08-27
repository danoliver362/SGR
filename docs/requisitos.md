RF-001 — Cadastro de cliente
O sistema deve permitir cadastrar o nome e telefone do cliente.

RF-002 — Consulta de cliente
O sistema deve permitir localizar um cliente por nome ou telefone.

RF-003 — Histórico do cliente
O sistema deve permitir consultar os atendimentos e serviços anteriores associados ao cliente.

RF-004 — Criação de atendimento
O sistema deve permitir registrar um novo atendimento para um cliente.

RF-005 — Múltiplos relógios
Um atendimento deve permitir associar um ou vários relógios do mesmo cliente.

RF-006 — Cadastro do relógio
O sistema deve permitir cadastrar um relógio associado a um atendimento.

RF-007 — Identificação do relógio
O sistema deve permitir registrar marca, modelo e características do relógio para facilitar sua identificação.

RF-008 — Características visuais
O sistema deve permitir registrar informações como tipo de relógio, material e cor da pulseira e características do mostrador.

RF-009 — Registro do serviço
O sistema deve permitir registrar o serviço realizado em cada relógio, independentemente de o atendimento ser concluído imediatamente ou exigir acompanhamento posterior.

RF-010 — Atendimento rápido
O sistema deve permitir registrar de forma simplificada serviços realizados e concluídos no momento do atendimento.

RF-011 — Status do serviço
O sistema deve permitir acompanhar o status atual de cada serviço.

RF-012 — Localização física
O sistema deve permitir registrar a localização física atual do relógio na loja.
Exemplo:
📍 Bancada
📍 Cabine
📍 Caixa de pendentes
📍 Gancho de prontos

RF-013 — Avaliação do serviço
O sistema deve permitir registrar o resultado da avaliação realizada no relógio.

RF-014 — Orçamento
O sistema deve permitir registrar quando um serviço necessita de orçamento e o valor estimado, quando disponível.

RF-015 — Aprovação do orçamento
O sistema deve permitir registrar a aprovação ou recusa do orçamento pelo cliente.

RF-016 — Necessidade de peça
O sistema deve permitir registrar quando a realização do serviço depende de uma peça.

RF-017 — Acompanhamento de pendências
O sistema deve permitir identificar serviços que estejam aguardando uma ação ou informação para continuar o atendimento.

Porque o seu exemplo acabou de mostrar que existem várias pendências:

🟡 aguardando orçamento;
🟡 aguardando aprovação do cliente;
🟡 aguardando peça;
🟡 aguardando resposta do cliente;
🟡 talvez outras que ainda vamos descobrir.


RF-018 — Prazo
O sistema deve permitir registrar e acompanhar o prazo estimado para conclusão do serviço.

RF-019 — Conclusão do serviço
O sistema deve permitir registrar que o serviço de um relógio foi concluído.

Isso é diferente de simplesmente mudar o status. Queremos que fique registrado que o trabalho realmente terminou.

RF-020 — Aviso ao cliente
O sistema deve permitir registrar que o cliente foi informado sobre a conclusão do serviço.

RF-021 — Aguardando retirada
O sistema deve identificar os relógios cujo serviço foi concluído e que estão aguardando retirada pelo cliente.
Isso conversa diretamente com o gancho que você me mostrou:
PRONTOS P/ RETIRADA

RF-022 — Registro da retirada
O sistema deve permitir registrar a data em que o relógio foi retirado pelo cliente.
Isso substitui uma das informações que hoje vocês escrevem manualmente no cartão.

RF-023 — Retirada parcial
O sistema deve permitir registrar a retirada de um ou mais relógios de um atendimento sem encerrar os demais relógios que ainda permanecem pendentes.
Exemplo:

João — 15 relógios

✅ 10 retirados
🛠️ 3 em conserto
⏳ 2 aguardando peça

O atendimento continua aberto até todos serem resolvidos.

RF-024 — Registro de garantia
O sistema deve permitir registrar o período de garantia aplicável ao serviço realizado.
No caso de vocês:
3 meses ou 6 meses.

RF-025 — Retorno em garantia
O sistema deve permitir registrar o retorno de um relógio relacionado a um serviço realizado anteriormente e consultar seu histórico de garantia.
