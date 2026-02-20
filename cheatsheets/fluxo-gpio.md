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
---

# Leitura rápida do fluxo

1. Defina o objetivo
2. Ache o periférico
3. Vá ao capítulo no TRM
4. Pegue endereço base
5. Identifique registradores
6. Configure bits
7. Implemente


---

# Ideia principal

👉 Sempre pense em investigação no manual antes do código.
