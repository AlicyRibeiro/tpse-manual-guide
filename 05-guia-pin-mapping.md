#  Guia de Pin Mapping — Do pino físico ao periférico

Este guia ensina como descobrir qual módulo de hardware controla um pino físico
da placa e como encontrar o identificador correto para usar no código.

O processo é essencial em qualquer projeto embarcado.

---

#  Problema que queremos resolver

Quando olhamos para a placa vemos:

👉 nomes de pinos físicos (ex: P8_12, D13, PA5)

Mas no código precisamos de:

👉 módulo + número do pino (ex: GPIO1_12)

Este guia mostra como fazer essa tradução.

---

#  Visão geral do processo

PINO FÍSICO → NOME DO SINAL → MÓDULO → BIT → REGISTRADOR

---

#  Passo a passo

## 1️⃣ Identifique o pino físico na placa

Use:

- silk da placa
- pinout oficial
- documentação da placa

Exemplo:

Pino → P8_12

---

## 2️⃣ Consulte a tabela de pinout

A tabela mostra:

- nome do sinal interno
- função padrão
- funções alternativas

Exemplo:

P8_12 → GPIO1_12

---

## 3️⃣ Identifique o módulo

O nome indica o módulo:

GPIO1_12 → módulo GPIO1

---

## 4️⃣ Identifique o número do bit

O número após o underscore é o bit:

GPIO1_12 → bit 12

Máscara:

```c
(1 << 12)
```
---

## 5️⃣ Verifique o pin mux

No TRM ou datasheet, confirme:

- modo de operação do pino
- função selecionada

Sem isso o periférico pode não funcionar.

---

# Exemplo completo
 ## Objetivo

Controlar o pino P8_12

## Descoberta

P8_12 → GPIO1_12

## Interpretação

Módulo → GPIO1
Bit → 12

 ## Uso no código

```
GPIO_OE &= ~(1 << 12);
GPIO_SETDATAOUT = (1 << 12);
```
---

# Onde encontrar as informações

## 📘 Datasheet da placa

Mostra pinout físico

## 📘 TRM do SoC

Mostra multiplexação e registradores

## 📄 Documentação da placa

Relaciona nomes físicos com sinais internos

---

# ⚠️ Erros comuns

* ❌ Confundir pino físico com número do GPIO
* ❌ Ignorar multiplexação
* ❌ Usar módulo errado
* ❌ Não verificar se o pino suporta aquela função

---

# Resumo

Pin mapping é a ponte entre:

- hardware físico ↔ registradores do sistema
- Dominar esse processo é essencial para trabalhar com qualquer placa.
