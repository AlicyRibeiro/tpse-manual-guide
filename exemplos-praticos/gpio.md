#  Exemplo prático: Configurando um GPIO (Bare-Metal)

Este guia mostra como encontrar no manual todas as informações necessárias para configurar um pino GPIO como saída e controlar seu estado.

O objetivo não é apenas configurar o pino, mas aprender **como navegar no TRM e entender o raciocínio**.

---

#  Objetivo

Configurar um pino GPIO como saída e escrever nível lógico alto (1).

Ao final, você saberá:

- Como identificar o módulo responsável
- Como encontrar o endereço base
- Como localizar registradores
- Como entender os campos de bits
- Como montar a sequência de configuração

---

#  Periférico responsável

Função desejada → Entrada/Saída digital  
Periférico responsável → **GPIO (General Purpose Input/Output)**  

O módulo GPIO permite:

- Configurar direção do pino
- Ler estado
- Escrever nível lógico

---

#  Onde encontrar no TRM

No TRM, procure por:

- **Capítulo do módulo GPIO**
- Seção **Memory Map**
- Seção **Register Summary**
- Seção **Functional Description**

Palavras-chave para busca no PDF:

- GPIO
- Memory Map
- Register Summary
- Direction
- Data



---

#  Memory Map

No capítulo do GPIO, encontramos:

- Endereço base do módulo
- Lista de registradores com offsets

📌 Fórmula usada:

ENDEREÇO DO REGISTRADOR = ENDEREÇO BASE + OFFSET

Exemplo hipotético:

- Base GPIO: `0x4804C000`
- Offset registrador de direção: `0x134`

Endereço final:

    0x4804C000 + 0x134 = 0x4804C134

  
---

#  Registradores importantes

## 📌 GPIO_OE (Output Enable)
Função: define se o pino é entrada ou saída  

- 0 → saída  
- 1 → entrada  

---

## 📌 GPIO_DATAOUT
Função: define o nível lógico do pino configurado como saída  

- 0 → nível baixo  
- 1 → nível alto  

---

## 📌 GPIO_SETDATAOUT
Função: seta bits para 1 sem afetar outros  

---

## 📌 GPIO_CLEARDATAOUT
Função: limpa bits (coloca 0) sem afetar outros  

---

#  Campos de bits

Cada pino corresponde a um bit no registrador.

Exemplo:

- Pino 21 → Bit 21  

### No GPIO_OE:
- Bit = 0 → saída  
- Bit = 1 → entrada  

### No DATAOUT:
- Bit = 1 → nível alto  
- Bit = 0 → nível baixo  

Tipo do campo: **R/W (leitura e escrita)**

---

#  Sequência de configuração

Passos típicos:

1. Habilitar clock do módulo GPIO
2. Configurar multiplexação do pino (pin mux)
3. Configurar direção como saída
4. Escrever nível lógico no pino  

---

#  Pseudocódigo

```c
// 1. habilitar clock do GPIO
habilitar_clock(GPIO);

// 2. configurar pino como saída
GPIO_OE &= ~(1 << PIN);

// 3. escrever nível alto
GPIO_SETDATAOUT = (1 << PIN);

```

# Neste exemplo vimos como:

- ✅ Identificar o periférico correto
- ✅ Navegar no capítulo do GPIO
- ✅ Encontrar endereço base e offsets
- ✅ Entender registradores
- ✅ Interpretar bits
- ✅ Transformar manual em passos

---

# Erros comuns

- ❌ Esquecer de habilitar o clock do periférico
- ❌ Não configurar o pin mux corretamente
- ❌ Usar endereço base errado
- ❌ Confundir registrador de direção com dados
- ❌ Escrever diretamente em DATAOUT sem máscara

---

# Conclusão
Configurar um GPIO não é apenas escrever código —
é seguir um processo de investigação no manual.

Quando você domina esse método, consegue trabalhar com qualquer periférico.
