#  GPIO Cheatsheet — Consulta Rápida

Este guia é um resumo rápido dos conceitos e passos necessários para configurar um GPIO em sistemas embarcados bare-metal.

Use quando você já entende o processo e só precisa relembrar rapidamente.

---

#  O que é GPIO?

GPIO (General Purpose Input/Output) é o periférico responsável por controlar pinos digitais.

Permite:

- ✔️ Ler sinais  
- ✔️ Escrever sinais  
- ✔️ Configurar direção  
- ✔️ Controlar hardware externo  

---

#  Passos rápidos para configurar um GPIO

1. Habilitar clock do módulo
2. Configurar multiplexação do pino (pin mux)
3. Configurar direção (entrada ou saída)
4. Ler ou escrever no registrador de dados  

---

#  Fórmula importante

ENDEREÇO = BASE + OFFSET

Sempre use isso para encontrar registradores no memory map.

---

#  Registradores mais comuns

## 📌 GPIO_OE
Define direção do pino  

- 0 → saída  
- 1 → entrada  

---

## 📌 GPIO_DATAIN
Lê estado do pino  

---

## 📌 GPIO_DATAOUT
Escreve estado do pino  

---

## 📌 GPIO_SETDATAOUT
Coloca bit em 1 sem alterar outros  

---

## 📌 GPIO_CLEARDATAOUT
Coloca bit em 0 sem alterar outros  

---

#  Regra dos bits

Cada pino = 1 bit no registrador  

Exemplo:

Pino 7 → Bit 7  

Máscara:

```c
(1 << PIN)
```

---

# Sequência típica (resumo)

```
habilitar_clock(GPIO);
configurar_mux(PIN);

GPIO_OE &= ~(1 << PIN);      // saída
GPIO_SETDATAOUT = (1 << PIN); // nível alto
```

---

# Erros clássicos

- ❌ Esquecer clock
- ❌ Não configurar pin mux
- ❌ Usar registrador errado
- ❌ Escrever sem máscara
- ❌ Confundir entrada e saída

---

#   Quando usar este cheatsheet

- ✅ Revisão rápida
- ✅ Durante implementação
- ✅ Antes de prova
- ✅ Debug

---

# Regra de ouro

👉 Sempre leia o TRM para confirmar nomes e endereços
👉 O cheatsheet é um guia, não substitui o manual
