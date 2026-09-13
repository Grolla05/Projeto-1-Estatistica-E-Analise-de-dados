# Eficiência Operacional em Linhas de Produção — Projeto I

Estudo estatístico sobre a eficiência operacional de linhas de produção industrial, desenvolvido para a disciplina de Estatística e Análise de Dados — Escola Politécnica, PUC-Campinas. O projeto investiga a relação entre o **nível de automação** das linhas, o **tempo de ciclo** produtivo e a **quantidade de unidades produzidas**, e é entregue em sprints incrementais ao longo do semestre.

## Sprints

| Sprint | Conteúdo | Pasta |
|---|---|---|
| **Sprint 1** | Estatística descritiva: tabelas de frequência, gráficos e medidas de tendência central (média, moda, mediana) das três variáveis | [`SPRINT_1/`](SPRINT_1) |
| **Sprint 2** | Medidas de dispersão e posição: quartis, percentis, boxplot e identificação de outliers das variáveis quantitativas | [`SPRINT_2/`](SPRINT_2) |

Cada pasta de sprint tem seu próprio README com o detalhamento da entrega, dos notebooks e de como executá-los.

## Base de Dados

**Localização:** [`refs/Eficiencia Operacional em Linhas de Producao.xlsx`](refs)

| Coluna | Tipo | Descrição |
|---|---|---|
| `Nivel_Automacao` | Texto (categórico ordinal) | Nível de automação da linha de produção (Baixa, Média, Alta) |
| `Tempo_Ciclo_s` | Numérico decimal | Tempo de ciclo produtivo, em segundos |
| `Unidades_Produzidas` | Numérico inteiro | Quantidade de unidades produzidas |

- **Dimensões:** 1.000 linhas × 3 colunas

## Estrutura do Repositório

```
Projeto-1-Estatistica-E-Analise-de-dados/
├── SPRINT_1/
│   ├── assets/                       # Notebooks-modelo do professor (referência)
│   ├── Nivel_Automacao.ipynb
│   ├── Tempo_ciclo.ipynb
│   ├── Unidades_Produzidas.ipynb
│   └── README.md
├── SPRINT_2/
│   ├── assets/                       # Notebooks-modelo do professor (referência)
│   ├── Tempo_Ciclo_Sprint2.ipynb
│   ├── Unidades_Produzidas_Sprint2.ipynb
│   └── README.md
├── refs/
│   └── Eficiencia Operacional em Linhas de Producao.xlsx   # Base de dados do projeto
├── .gitignore
├── requirements.txt
└── README.md                          # este arquivo
```

## Tecnologias e Bibliotecas Utilizadas

[![My Skills](https://skillicons.dev/icons?i=python,pycharm)](https://skillicons.dev)

- **pandas** — leitura da planilha (`.xlsx`) e manipulação dos dados
- **math** — apoio a cálculos estatísticos (Sprint 1)
- **numpy** / **scipy** — apoio a cálculos numéricos e medidas de dispersão (Sprint 2)
- **seaborn** — gráficos de contagem, histogramas e boxplots
- **matplotlib.pyplot** — construção e formatação de gráficos
- **openpyxl** — leitura de arquivos `.xlsx` via `pandas`

## Como Executar

1. **Criar/ativar o ambiente virtual**: `python -m venv .venv` e depois ativá-lo
2. **Instalar as dependências**: `pip install -r requirements.txt`
3. **Abrir os notebooks** (Jupyter Notebook, JupyterLab, VS Code ou Google Colab) dentro da pasta da sprint desejada
4. **Executar cada notebook do início ao fim** ("Restart Kernel and Run All"), conferindo o caminho de leitura da planilha (`refs/Eficiencia Operacional em Linhas de Producao.xlsx`, ajustando o caminho relativo conforme a pasta do notebook)
5. Consultar o README de cada sprint para a ordem de execução recomendada e os detalhes de cada entrega

## Equipe

**Grupo 6** — Escola Politécnica, PUC-Campinas

| Nome                      | RA |
|---------------------------|-----|
| Eduarda Barbosa Kauffmann | 24004761 |
| Felipe Grolla Freitas     | 24004846 |
| Vitória Marques Pires     | 24011312 |
