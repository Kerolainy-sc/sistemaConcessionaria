# Sistema de Avaliação de Crédito Veicular — Concessionária Mercedes-Benz

##  Sobre o Projeto

*Este projeto consiste em um sistema de console desenvolvido em **Linguagem C** para automatizar o fluxo de atendimento, cadastro de clientes e análise preliminar de crédito financeiro em uma concessionária automotiva.*

*O sistema avalia a capacidade financeira do cliente em relação ao modelo de veículo selecionado, aplicando parâmetros percentuais sobre a renda mensal informada e gerando relatórios quantitativos consolidados ao término das operações.*



## ╰┈➤ Funcionalidades

```
- **Gerenciamento de Lotes:** Permite o processamento de múltiplos cadastros de clientes em ciclos contínuos de atendimento.
- **Entrada Segura:** Coleta de dados pessoais e de contato utilizando `fgets()` para prevenir estouros de buffer (*buffer overflow*).
- **Catálogo Interativo:** Exibição de um menu com 10 modelos de veículos da marca (variando de veículos de entrada a utilitários esportivos e superesportivos de alto luxo).
- **Motor de Análise de Crédito:** Avaliação automatizada com base em regras percentuais de renda:
  - **Aprovado:** $\text{Renda Mensal} \ge 30\% \text{ do Valor do Veículo}$
  - **Em Análise:** $15\% \le \text{Renda Mensal} < 30\% \text{ do Valor do Veículo}$ (Requer fiador ou entrada complementar)
  - **Reprovado:** $\text{Renda Mensal} < 15\% \text{ do Valor do Veículo}$ (Oferece a opção interativa de tentar outro modelo)
- **Relatório Final:** Apresentação estatística consolidada com o somatório de aprovações, análises pendentes e reprovações.
```
---

## 📊 Regras de Negócio e Lógica

| Status | Condição Matemática | Comportamento do Sistema |
| :--- | :--- | :--- |
| **Aprovado** | $\text{Renda} \ge 0.30 \times \text{Preço}$ | Finaliza a análise com sucesso e computa a aprovação. |
| **Em Análise** | $0.15 \times \text{Preço} \le \text{Renda} < 0.30 \times \text{Preço}$ | Informa exigência de garantias e computa a pendência. |
| **Negado** | $\text{Renda} < 0.15 \times \text{Preço}$ | Informa insuficiência e permite reavaliar outro modelo. |

---

## 💻 Aspectos Técnicos

````
- Utilização de estruturas de controle de fluxo otimizadas (`while`, `for`, `do-while`).
- Emprego de desvios condicionais com `switch-case` para o catálogo e códigos de status.
- Gerenciamento adequado do buffer de entrada do teclado (`getchar()`) para mitigar conflitos entre leituras numéricas (`scanf`) e textuais (`fgets`).
````
1. Clone o repositório ou baixe o arquivo fonte (`.c`).
2. Abra o terminal na pasta onde o arquivo está salvo.
3. Compile o código:
   ```bash
   gcc main.c -o concessionaria
