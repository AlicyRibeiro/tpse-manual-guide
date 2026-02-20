#  Como identificar o periférico correto

Antes de procurar registradores ou endereços no TRM, o primeiro passo é
descobrir qual periférico do sistema é responsável pela funcionalidade desejada.

Este guia ensina um método simples e replicável para fazer isso.

---

#  Por que isso é importante

Muitos erros em sistemas embarcados acontecem porque o desenvolvedor:

❌ procura no módulo errado  
❌ confunde periféricos  
❌ tenta configurar registradores incorretos  

Saber identificar o periférico economiza tempo e evita frustração.

---

#  Passo 1 — Defina claramente o que você quer fazer

Sempre comece com uma frase simples:

👉 "Quero ______"

Exemplos:

- Ler um botão  
- Acender um LED  
- Enviar dados pela serial  
- Gerar um sinal PWM  
- Medir tempo  

---

#  Passo 2 — Classifique a funcionalidade

Associe o problema a uma categoria de hardware.

| Funcionalidade | Tipo de periférico |
|----------------|-------------------|
| Entrada/Saída digital | GPIO |
| Comunicação serial | UART |
| Comunicação síncrona | SPI / I2C |
| Temporização | Timers |
| Geração de sinal | PWM |
| Eventos externos | Interrupções |
| Conversão analógica | ADC |

---

#  Passo 3 — Consulte o diagrama de blocos do SoC

O block diagram mostra:

- Quais módulos existem
- Como eles se conectam
- Qual é o nome oficial do periférico

👉 Isso evita procurar pelo nome errado no TRM.

---

#  Passo 4 — Confirme no datasheet

O datasheet ajuda a descobrir:

- Se o periférico está disponível no dispositivo
- Quais pinos suportam aquela função
- Limitações do hardware

---

#  Passo 5 — Só então vá para o TRM

Agora sim você sabe:

✔️ Nome do módulo  
✔️ Função do periférico  
✔️ Onde procurar  

A busca no TRM fica muito mais rápida.

---

#  Fluxo resumido

OBJETIVO → CATEGORIA → PERIFÉRICO → DATASHEET → TRM

---

#  Exemplos práticos

##  Exemplo 1 — Acender um LED

Objetivo: controlar nível lógico  

Categoria: Entrada/Saída digital  

Periférico: GPIO  

---

##  Exemplo 2 — Ler um botão

Objetivo: ler estado de pino  

Categoria: Entrada digital  

Periférico: GPIO  

---

##  Exemplo 3 — Enviar dados para o PC

Objetivo: comunicação serial  

Categoria: Comunicação  

Periférico: UART  

---

##  Exemplo 4 — Criar atraso preciso

Objetivo: temporização  

Categoria: Tempo  

Periférico: Timer  

---

#  Erros comuns

❌ Confundir UART com USB  
❌ Usar GPIO para gerar PWM (quando há módulo específico)  
❌ Ignorar multiplexação de pinos  
❌ Não verificar se o periférico existe no modelo do chip  

---

#  Dica profissional

Engenheiros experientes raramente começam pelo TRM.

Eles começam pelo:

👉 problema  
👉 diagrama do sistema  
👉 datasheet  

Só depois vão para registradores.

---

#  Resumo

Identificar o periférico é o primeiro passo do processo de investigação.

Quando você domina essa etapa:

✔️ encontra informações mais rápido  
✔️ entende melhor o sistema  
✔️ evita configurações erradas  

---

#  Próximo passo

Depois de identificar o periférico, siga para:

👉 método de busca no TRM  
👉 exemplo prático do módulo  
