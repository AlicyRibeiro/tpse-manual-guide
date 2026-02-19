#  Fluxo para configurar um GPIO 

```text
OBJETIVO
  │
  ▼
Qual pino quero usar?
  │
  ▼
Qual periférico controla?
  │
  └──► GPIO
          │
          ▼
Encontrar capítulo no TRM
          │
          ▼
Memory Map
(BASE + OFFSET)
          │
          ▼
Registradores
(GPIO_OE, DATAOUT, DATAIN…)
          │
          ▼
Campos de bits
(bit do pino)
          │
          ▼
Sequência de configuração
(Clock → Mux → Direção → Dados)
          │
          ▼
CÓDIGO

```
