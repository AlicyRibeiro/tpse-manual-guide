#  Arquitetura do SoC AM335x (Visão Simplificada)

Este diagrama mostra como os principais blocos do sistema se conectam.
Ele serve como um mapa mental para entender a relação entre CPU,
barramentos e periféricos.

O objetivo é facilitar a navegação no TRM.

---

#  Visão geral

O AM335x segue o modelo clássico de SoC:

CPU → Barramento → Periféricos → Registradores

---

#  Diagrama simplificado

```text
                    ┌──────────────────────┐
                    │        CPU           │
                    │     ARM Cortex-A8    │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Interconnect /     │
                    │     Barramentos      │
                    └──────────┬───────────┘
                               │
     ┌───────────────┬─────────┼─────────┬───────────────┐
     ▼               ▼         ▼         ▼               ▼

┌──────────┐  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐
│  Control │  │  Clock   │ │  GPIO    │ │   UART   │ │  Timers  │
│  Module  │  │  Module  │ │ Modules  │ │ Modules  │ │ Modules  │
└──────────┘  └──────────┘ └──────────┘ └──────────┘ └──────────┘

     │
     ▼
┌──────────┐
│ Pin Mux  │
└──────────┘

```

---

# Papel de cada bloco
 CPU

Executa o software e acessa registradores via memória.

---

#  Barramentos

Conectam a CPU aos periféricos.

Permitem acesso memory-mapped.

---

# Control Module

Gerencia:

- multiplexação de pinos
- configurações elétricas
- seleção de função dos pinos

---

# Clock Module

Responsável por habilitar clocks dos periféricos.

Sem clock → periférico inativo.

---

# GPIO

Entrada e saída digital.

---

# UART

Comunicação serial.

---

# Timers

Base de tempo e eventos periódicos.

---

# aminho de um acesso a registrador

Quando o código escreve em um registrador:

* 1️⃣ CPU executa instrução
* 2️⃣ Endereço vai para o barramento
* 3️⃣ Barramento roteia para o periférico
* 4️⃣ Periférico altera estado interno

---

# Como isso ajuda a ler o TRM

Com essa visão você entende:

* ✔️ Por que precisa habilitar clock
* ✔️ Por que configurar pin mux
* ✔️ Por que periféricos têm endereços base
* ✔️ Como módulos são independentes

---

# Resumo

O sistema funciona como camadas:

Software → CPU → Barramento → Periférico → Hardware

Quando você entende essa cadeia, a leitura do manual deixa de ser confusa
e passa a fazer sentido lógico.
