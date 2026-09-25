# Modelo Lógico do Sistema — SGR

## 1. Tabelas

### 1.1 CLIENTE

Representa o cliente da relojoaria.

| Campo | Tipo | Restrições |
|---|---|---|
| ID | INT | PK |
| NOME | VARCHAR(100) | NOT NULL |
| TELEFONE | VARCHAR(20) | NOT NULL |

**Regras:**
- O telefone pode se repetir entre diferentes clientes.
- `ID` identifica unicamente o cliente.

---

### 1.2 ATENDIMENTO

Representa cada atendimento realizado ao cliente.

| Campo | Tipo | Restrições |
|---|---|---|
| ID | INT | PK |
| NUMERO | VARCHAR(10) | NOT NULL, UNIQUE |
| DATA | DATE | NOT NULL |
| STATUS | VARCHAR(20) | NOT NULL |
| CLIENTE_ID | INT | NOT NULL, FK |

**Chave estrangeira:**
- `CLIENTE_ID` → `CLIENTE.ID`

**Valores previstos para STATUS:**
- `ABERTO`
- `ENCERRADO`

**Regras:**
- `NUMERO` é único e representa o número utilizado pela relojoaria para localizar o atendimento.
- `ID` é o identificador interno da tabela.

---

### 1.3 ITEM_ATENDIMENTO

Representa a participação de um relógio específico em um atendimento.

| Campo | Tipo | Restrições |
|---|---|---|
| ID | INT | PK |
| ESTADO_CONSERVACAO | VARCHAR(100) | NOT NULL |
| LOCALIZACAO_FISICA | VARCHAR(20) | NULL |
| DATA_RETIRADA | DATE | NULL |
| ATENDIMENTO_ID | INT | NOT NULL, FK |
| RELOGIO_ID | INT | NOT NULL, FK |

**Chaves estrangeiras:**
- `ATENDIMENTO_ID` → `ATENDIMENTO.ID`
- `RELOGIO_ID` → `RELOGIO.ID`

**Regras:**
- O estado de conservação deve ser registrado na entrada do relógio.
- A localização física pode ser preenchida posteriormente.
- `DATA_RETIRADA` permanece nula enquanto o relógio não for retirado.

---

### 1.4 RELOGIO

Representa o relógio cadastrado no sistema.

| Campo | Tipo | Restrições |
|---|---|---|
| ID | INT | PK |
| MARCA | VARCHAR(50) | NOT NULL |
| MODELO | VARCHAR(100) | NOT NULL |
| TIPO | VARCHAR(50) | NOT NULL |
| MATERIAL_PULSEIRA | VARCHAR(50) | NULL |
| COR_PULSEIRA | VARCHAR(30) | NULL |
| CARACTERISTICAS_MOSTRADOR | VARCHAR(255) | NULL |

**Regras:**
- Marca, modelo e tipo são obrigatórios.
- Material, cor da pulseira e características do mostrador são opcionais.

---

### 1.5 SERVICO

Representa um serviço relacionado a um item de atendimento.

| Campo | Tipo | Restrições |
|---|---|---|
| ID | INT | PK |
| DESCRICAO | VARCHAR(255) | NOT NULL |
| DATA_INICIO | DATE | NOT NULL |
| DATA_PREVISTA_CONCLUSAO | DATE | NULL |
| DATA_CONCLUSAO | DATE | NULL |
| STATUS | VARCHAR(20) | NOT NULL |
| VALOR | DECIMAL(10,2) | NULL |
| POSSUI_GARANTIA | BOOLEAN | NOT NULL |
| INICIO_GARANTIA | DATE | NULL |
| FIM_GARANTIA | DATE | NULL |
| ITEM_ATENDIMENTO_ID | INT | NOT NULL, FK |
| ITEM_ORCAMENTO_ID | INT | NULL, UNIQUE, FK |

**Chaves estrangeiras:**
- `ITEM_ATENDIMENTO_ID` → `ITEM_ATENDIMENTO.ID`
- `ITEM_ORCAMENTO_ID` → `ITEM_ORCAMENTO.ID`

**Valores previstos para STATUS:**
- `AGUARDANDO`
- `EM_ANDAMENTO`
- `CONCLUIDO`
- `CANCELADO`

**Regras:**
- `VALOR` pode ser nulo enquanto o valor do serviço ainda não estiver definido.
- `DATA_PREVISTA_CONCLUSAO` pode ser nula enquanto não houver uma previsão.
- `DATA_CONCLUSAO` permanece nula enquanto o serviço não for concluído.
- Se `POSSUI_GARANTIA` for `FALSE`, `INICIO_GARANTIA` e `FIM_GARANTIA` devem ser nulos.
- Se `POSSUI_GARANTIA` for `TRUE`, `INICIO_GARANTIA` e `FIM_GARANTIA` devem ser preenchidos.
- `ITEM_ORCAMENTO_ID` pode ser nulo porque um serviço pode ser realizado diretamente, sem orçamento.
- `ITEM_ORCAMENTO_ID` é `UNIQUE` porque um item de orçamento pode originar no máximo um serviço.

---

### 1.6 ORCAMENTO

Representa uma proposta de serviços apresentada ao cliente.

| Campo | Tipo | Restrições |
|---|---|---|
| ID | INT | PK |
| DATA | DATE | NOT NULL |
| ITEM_ATENDIMENTO_ID | INT | NOT NULL, UNIQUE, FK |

**Chave estrangeira:**
- `ITEM_ATENDIMENTO_ID` → `ITEM_ATENDIMENTO.ID`

**Regras:**
- Um item de atendimento pode possuir no máximo um orçamento.
- O orçamento não possui um campo `STATUS`.
- A situação geral do orçamento é determinada pelos status de seus itens.

---

### 1.7 ITEM_ORCAMENTO

Representa cada item proposto dentro de um orçamento.

| Campo | Tipo | Restrições |
|---|---|---|
| ID | INT | PK |
| DESCRICAO | VARCHAR(255) | NOT NULL |
| VALOR | DECIMAL(10,2) | NULL |
| STATUS | VARCHAR(20) | NOT NULL |
| ORCAMENTO_ID | INT | NOT NULL, FK |

**Chave estrangeira:**
- `ORCAMENTO_ID` → `ORCAMENTO.ID`

**Valores previstos para STATUS:**
- `PENDENTE`
- `APROVADO`
- `RECUSADO`

**Regras:**
- Cada item pertence a um orçamento.
- `VALOR` pode ser nulo enquanto o valor da proposta ainda não estiver definido.
- Cada item pode gerar no máximo um serviço.

---

### 1.8 PAGAMENTO

Representa um pagamento realizado referente a um atendimento.

| Campo | Tipo | Restrições |
|---|---|---|
| ID | INT | PK |
| VALOR | DECIMAL(10,2) | NOT NULL |
| FORMA_PAGAMENTO | VARCHAR(30) | NOT NULL |
| DATA | DATE | NOT NULL |
| ATENDIMENTO_ID | INT | NOT NULL, FK |

**Chave estrangeira:**
- `ATENDIMENTO_ID` → `ATENDIMENTO.ID`

**Regras:**
- Um atendimento pode possuir vários pagamentos.
- Um atendimento pode ter pagamentos utilizando diferentes formas de pagamento.
- `VALOR`, `FORMA_PAGAMENTO` e `DATA` são obrigatórios.

---

## 2. Relacionamentos

### CLIENTE → ATENDIMENTO

**Cardinalidade: `1 : 0..N`**

A tabela `ATENDIMENTO` possui a FK `CLIENTE_ID`.

---

### ATENDIMENTO → ITEM_ATENDIMENTO

**Cardinalidade: `1 : N`**

A tabela `ITEM_ATENDIMENTO` possui a FK `ATENDIMENTO_ID`.

---

### ITEM_ATENDIMENTO → RELOGIO

**Cardinalidade: `N : 1`**

A tabela `ITEM_ATENDIMENTO` possui a FK `RELOGIO_ID`.

---

### ITEM_ATENDIMENTO → SERVICO

**Cardinalidade: `1 : 0..N`**

A tabela `SERVICO` possui a FK `ITEM_ATENDIMENTO_ID`.

---

### ATENDIMENTO → PAGAMENTO

**Cardinalidade: `1 : 0..N`**

A tabela `PAGAMENTO` possui a FK `ATENDIMENTO_ID`.

---

### ITEM_ATENDIMENTO → ORCAMENTO

**Cardinalidade: `1 : 0..1`**

A tabela `ORCAMENTO` possui a FK `ITEM_ATENDIMENTO_ID`, com restrição `UNIQUE`.

---

### ORCAMENTO → ITEM_ORCAMENTO

**Cardinalidade: `1 : N`**

A tabela `ITEM_ORCAMENTO` possui a FK `ORCAMENTO_ID`.

---

### ITEM_ORCAMENTO → SERVICO

**Cardinalidade: `0..1 : 0..1`**

A tabela `SERVICO` possui a FK opcional `ITEM_ORCAMENTO_ID`, com restrição `UNIQUE`.

Isso permite que um serviço seja originado de um item de orçamento ou seja criado diretamente.

---

## 3. Regras de Integridade

### Garantia do serviço

- Se `POSSUI_GARANTIA = FALSE`, `INICIO_GARANTIA` e `FIM_GARANTIA` devem ser `NULL`.
- Se `POSSUI_GARANTIA = TRUE`, `INICIO_GARANTIA` e `FIM_GARANTIA` devem ser preenchidos.

### Orçamento

- Um `ITEM_ATENDIMENTO` pode possuir no máximo um `ORCAMENTO`.
- Um `ORCAMENTO` possui um ou mais `ITEM_ORCAMENTO`.
- O estado geral do orçamento é obtido a partir dos status de seus itens.

### Serviço originado de orçamento

- Um `ITEM_ORCAMENTO` pode originar no máximo um `SERVICO`.
- Um `SERVICO` pode existir sem `ITEM_ORCAMENTO`, representando um serviço realizado diretamente.

### Pagamentos

- Um `ATENDIMENTO` pode possuir nenhum ou vários `PAGAMENTO`.
- Um atendimento pode possuir mais de um pagamento e utilizar diferentes formas de pagamento.
