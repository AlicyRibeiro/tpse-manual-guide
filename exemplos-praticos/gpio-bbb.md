#  GPIO na BeagleBone Black (AM335x) — Exemplo real

Este exemplo mostra como localizar no TRM do AM335x as informações necessárias
para configurar um GPIO como saída.

---

#  Objetivo

Configurar um pino do módulo GPIO1 como saída e colocar nível lógico alto.

---

#  Periférico

Entrada/Saída digital → GPIO  

O AM335x possui múltiplos módulos GPIO:
- GPIO0
- GPIO1
- GPIO2
- GPIO3

---

#  Endereço base (AM335x)

GPIO1 BASE ADDRESS:

    0x4804C000


---

#  Registradores importantes

## 📌 GPIO_OE (Offset 0x134)

Define direção:

- 0 → saída
- 1 → entrada

Endereço:

    0x4804C000 + 0x134 = 0x4804C134


---

## 📌 GPIO_SETDATAOUT (Offset 0x194)

Coloca nível alto

Endereço:

    0x4804C000 + 0x194 = 0x4804C194



---

## 📌 GPIO_CLEARDATAOUT (Offset 0x190)

Coloca nível baixo

Endereço:


    0x4804C000 + 0x190 = 0x4804C190


---

#  Bits

Cada pino = 1 bit

Exemplo:

GPIO1_21 → bit 21

Máscara:

```c
(1 << 21)
```
---

# Sequência real

1. Habilitar clock do GPIO1 (CM_PER_GPIO1_CLKCTRL)
2. Configurar pin mux no Control Module
3. Configurar direção no GPIO_OE
4. Escrever no GPIO_SETDATAOUT

---

# Exemplo conceitual

```
#define GPIO1_BASE 0x4804C000
#define GPIO_OE (*(volatile unsigned int *)(GPIO1_BASE + 0x134))
#define GPIO_SETDATAOUT (*(volatile unsigned int *)(GPIO1_BASE + 0x194))

int pin = 21;

// saída
GPIO_OE &= ~(1 << pin);

// nível alto
GPIO_SETDATAOUT = (1 << pin);
```

---

# O que este exemplo ensina

- ✅ Como usar endereço real
- ✅ Como aplicar BASE + OFFSET
- ✅ Como mapear pino para bit
- ✅ Como transformar TRM em código

---

# Observações importantes

- ✔️ Sempre habilite o clock antes
- ✔️ Configure o pin mux corretamente
- ✔️ Confirme o módulo GPIO do pino usado

---

# Conclusão

Depois que você entende o processo no AM335x,
o mesmo raciocínio funciona para qualquer microcontrolador.

