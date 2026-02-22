# TPSE Manual Guide
Como aprender a navegar em Datasheets e TRMs na prática

Guia prático para estudantes de Sistemas Embarcados aprenderem a encontrar informações em manuais técnicos (datasheets e Technical Reference Manuals — TRM) e transformá-las em configurações reais de hardware em nível bare-metal.

Este repositório foca no que normalmente não é ensinado de forma explícita:


👉 o processo mental para investigar o manual e descobrir como configurar um periférico.

---

# Objetivo

Ensinar um método replicável para responder perguntas comuns no desenvolvimento embarcado:

- Onde encontro o endereço base de um periférico?
- Como identificar os registradores necessários?
- Como interpretar campos de bits?
- Como transformar o manual em uma sequência de configuração?

A ideia é que, ao final, você consiga navegar em qualquer TRM com segurança.

---

# O que você vai aprender

- ✔️ Diferença entre Datasheet, TRM e User Guide
- ✔️ Como identificar o periférico correto para um problema
- ✔️ Como usar o memory map
- ✔️ Como localizar registradores e offsets
- ✔️ Como interpretar tabelas de bits
- ✔️ Como montar a sequência de inicialização
- ✔️ Como transformar documentação em código

---

# Estrutura do repositório

```
tpse-manual-guide/
│
├── README.md
├── 03-metodo-de-busca.md        → Método universal de navegação em manuais
│
├── exemplos-praticos/
│   ├── gpio.md                  → Exemplo guiado genérico
│   └── gpio-bbb.md              → Exemplo real com endereços
│
├── cheatsheets/
│   ├── gpio-cheatsheet.md       → Consulta rápida de registradores
│   └── fluxo-gpio.md            → Mapa mental do processo
│
└── LICENSE

```

---

# Como usar este repositório

1. Encontre o periférico ou registrador que você precisa
2. Abra o exemplo correspondente em `/examples`
3. Veja:
   - Onde a informação foi encontrada no manual
   - Como interpretar os bits
   - Como aplicar no código

---

# Caminho rápido (consulta)

Se você já entende o processo:

👉 vá direto para a pasta cheatsheets

---

# Tecnologias e contexto

Os exemplos utilizam conceitos comuns a SoCs e microcontroladores modernos:

- Memory-mapped I/O
- Registradores de controle
- Configuração de clock
- Multiplexação de pinos
- Manipulação de bits

O método apresentado é independente de arquitetura e pode ser aplicado a qualquer plataforma.

---

# Roadmap

Planejamento de expansão do conteúdo:

 - Exemplo completo de UART
 - Exemplo de Timers
 - Interrupções passo a passo
 - Guia de pin mapping
 - Como entender clock tree
 - Cheatsheet de leitura de tabelas de registradores

 ---

# Contribuindo

Contribuições são bem-vindas!

Ideias úteis:

- Novos exemplos práticos
- Correções de explicações
- Diagramas e ilustrações
- Cheatsheets adicionais

Se você já teve dificuldade para achar algo em um manual,
isso provavelmente pode virar um ótimo material aqui.

---

# Apoie o projeto

Se este repositório te ajudar nos estudos ou no desenvolvimento,
considere dar uma ⭐ para que mais pessoas encontrem o material.

---

