# O Problema do Serviço de Catering

> Modelagem e resolução do clássico **catering service problem** (Prager, 1956) como um problema de **Programação Linear Inteira (PLI)** sobre uma rede de **transbordo (transshipment)**, implementado em Python com Google OR-Tools (SCIP).

Este repositório contém o material utilizado no seminário sobre o **Capítulo 18** do livro-texto que apresenta o problema do catering. Inclui:

- A formulação tradicional do problema (PLI).
- A reformulação como rede de transbordo.
- A aplicação do algoritmo simplex em rede.
- Análise de sensibilidade sobre preços e demanda.
- Implementação computacional com [Google OR-Tools](https://developers.google.com/optimization) usando o solver **SCIP**.

---

## O problema, em poucas palavras

Uma empresa de catering tem contratado fornecer refeições durante **7 dias consecutivos**, e a cada refeição entrega um **guardanapo limpo**. A demanda diária é conhecida:

| Dia | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|---|
| Guardanapos | 23 | 14 | 19 | 21 | 18 | 14 | 15 |

A cada dia, o caterer deve decidir:

- **Comprar** guardanapos novos a US\$ 3,00 cada;
- Enviar guardanapos sujos para **lavagem rápida** (2 dias, US\$ 0,75) ou **lavagem lenta** (4 dias, US\$ 0,50);
- **Reter** guardanapos sujos para o dia seguinte (sem custo).

O caterer começa **sem nenhum guardanapo**. O objetivo é encontrar a sequência de decisões que **minimiza o custo total** ao longo do horizonte de planejamento.

**Solução ótima:** US\$ 182,75.

---

## Estrutura do repositório

```
.
├── catering service.ipynb   # Notebook principal (modelagem + análise)
├── requirements.txt         # Dependências Python
├── LICENSE                  # Licença MIT
├── .gitignore               # Arquivos locais ignorados pelo repositório
└── README.md                # Este arquivo
```

O notebook está organizado em três grandes blocos:

1. **Formulação tradicional** — declaração de variáveis, função objetivo, restrições de demanda e balanço de sujos, resolução com OR-Tools/SCIP.
2. **Formulação como problema de transbordo** — equivalência com o modelo de fluxo em rede, com diagrama da rede em Mermaid.
3. **Algoritmo simplex em rede e análise de sensibilidade** — execução passo a passo do algoritmo e estudo do impacto de variações nos parâmetros.

---

## Como executar

### Pré-requisitos

- **Python 3.10+** (o notebook usa `match-case`, sintaxe disponível a partir do Python 3.10)
- `pip` atualizado

### Passo a passo

**1. Clone o repositório:**

```bash
git clone https://github.com/SEU_USUARIO/NOME_DO_REPO.git
cd NOME_DO_REPO
```

**2. Crie e ative um ambiente virtual:**

Linux/macOS:

```bash
python3 -m venv venv
source venv/bin/activate
```

Windows (PowerShell):

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

**3. Instale as dependências:**

```bash
pip install -r requirements.txt
```

**4. Abra o notebook:**

```bash
jupyter lab "catering service.ipynb"
```

ou, se preferir o Jupyter clássico:

```bash
jupyter notebook "catering service.ipynb"
```

> 💡 Os diagramas de rede são renderizados em Mermaid. JupyterLab 4.1+ suporta Mermaid nativamente; em versões mais antigas, pode ser necessária a extensão `jupyterlab-mermaid`.

---

## Tecnologias

- **[OR-Tools](https://developers.google.com/optimization)** — biblioteca de otimização do Google.
- **[SCIP](https://www.scipopt.org/)** — solver de programação inteira mista, acessado via OR-Tools.
- **Jupyter** — ambiente interativo para apresentação.

### Por que SCIP?

O SCIP é um dos solvers open-source mais robustos para PLI. Embora o problema do catering tenha matriz totalmente unimodular (e portanto sua relaxação contínua já produz solução inteira), o uso do SCIP via OR-Tools mantém a flexibilidade para extensões e generalizações que não preservam essa propriedade.

---

## Referência

O problema é apresentado no Capítulo 18 do livro:

> **Den Hertog, D., Roos, K., Terlaky, T.** *Linear Optimization: Models and Methods.*

Baseado no artigo clássico:

> **Prager, W.** (1956). "On the caterer problem." *Management Science*, 3(1), 15–23.

---

## Licença

Distribuído sob a **Licença MIT** — veja o arquivo [LICENSE](LICENSE) para detalhes.
