# Eficiência Operacional em Linhas de Produção — Projeto I / Sprint 2

Segunda entrega (SPRINT 2) do Projeto I da disciplina de Estatística e Análise de Dados — Escola Politécnica, PUC-Campinas. Avança sobre a análise descritiva da Sprint 1 aplicando **medidas de dispersão e posição** — quartis, percentis, boxplot e identificação de outliers — às duas variáveis quantitativas do estudo (`Tempo_Ciclo_s` e `Unidades_Produzidas`).

## Contextualização

Na Sprint 1, o grupo caracterizou a distribuição das três variáveis (`Nivel_Automacao`, `Tempo_Ciclo_s`, `Unidades_Produzidas`) por meio de tabelas de frequência, gráficos e medidas de tendência central. A Sprint 2 aprofunda essa análise nas variáveis quantitativas, investigando a **dispersão e a presença de valores atípicos (outliers)** nos dados de tempo de ciclo e unidades produzidas — informação relevante para avaliar a estabilidade do processo produtivo além da média.

- **Objetivo:** calcular quartis (Q1, Q2/mediana, Q3) e o intervalo interquartil (AIQ) de cada variável quantitativa, representá-las via boxplot e identificar/isolar observações que estejam fora dos limites inferior e superior (`Q1 − 1,5·AIQ` e `Q3 + 1,5·AIQ`).
- **Tamanho da amostra:** 1.000 observações, mesma base de dados da Sprint 1.
- **Variável qualitativa (`Nivel_Automacao`)**: não é tratada nesta sprint — medidas de dispersão por quartis/boxplot aplicam-se apenas às variáveis quantitativas.

## Variáveis do Estudo

| Variável | Coluna no arquivo | Classificação | Notebook final |
|---|---|---|---|
| Tempo de Ciclo | `Tempo_Ciclo_s` | Quantitativa Contínua (segundos) | [`Tempo_Ciclo_Sprint2.ipynb`](Tempo_Ciclo_Sprint2.ipynb) |
| Unidades Produzidas | `Unidades_Produzidas` | Quantitativa Discreta (contagem) | [`Unidades_Produzidas_Sprint2.ipynb`](Unidades_Produzidas_Sprint2.ipynb) |

## Estrutura do Projeto

```
SPRINT_2/
├── assets/
│   ├── 5 - Quartis_e_Percentis_BoxPlot_e_Outliers.ipynb   # Notebook modelo do professor (referência)
│   └── 6 - Medidas_de_Dispersão.ipynb                     # Notebook modelo do professor (referência)
├── Tempo_Ciclo_Sprint2.ipynb                              # Notebook — quartis, boxplot e outliers de Tempo_Ciclo_s
├── Unidades_Produzidas_Sprint2.ipynb                      # Notebook — quartis, boxplot e outliers de Unidades_Produzidas
└── README.md
```

### O que cada arquivo faz

- **`Tempo_Ciclo_Sprint2.ipynb`** — Lê a base de dados, executa `describe()` da variável, calcula Q1 (25%), Q2/mediana (50%) e Q3 (75%), constrói o boxplot (`seaborn`), calcula o intervalo interquartil (AIQ = Q3 − Q1) e os limites inferior/superior (`Q1 − 1,5·AIQ`, `Q3 + 1,5·AIQ`), e isola as linhas da base que estão acima do limite superior ou abaixo do limite inferior (outliers).
- **`Unidades_Produzidas_Sprint2.ipynb`** — Mesma metodologia aplicada à variável `Unidades_Produzidas`.
- **`assets/`** — Notebooks de referência fornecidos pelo professor (quartis/percentis/boxplot/outliers e medidas de dispersão), usados como apoio metodológico durante o desenvolvimento; não fazem parte da entrega.

> ⚠️ **Observação sobre o caminho dos dados:** os notebooks desta sprint leem o arquivo como `'Eficiencia Operacional em Linhas de Producao.xlsx'` (caminho relativo à própria pasta `SPRINT_2/`). Como a planilha está versionada em [`../refs/Eficiencia Operacional em Linhas de Producao.xlsx`](../refs), é necessário **copiar o arquivo para dentro de `SPRINT_2/`** antes de rodar, ou ajustar a leitura para `pd.read_excel('../refs/Eficiencia Operacional em Linhas de Producao.xlsx')`.

## Base de Dados

Mesma base da Sprint 1 — [`../refs/Eficiencia Operacional em Linhas de Producao.xlsx`](../refs) — 1.000 linhas × 3 colunas (`Nivel_Automacao`, `Tempo_Ciclo_s`, `Unidades_Produzidas`).

## Tecnologias e Bibliotecas Utilizadas

[![My Skills](https://skillicons.dev/icons?i=python,pycharm)](https://skillicons.dev)

- **pandas** — leitura da planilha e manipulação dos dados (`.describe()`, `.quantile()`)
- **numpy** — apoio a cálculos numéricos
- **scipy** (`scipy.stats.variation`) — apoio a medidas de dispersão relativa
- **seaborn** — construção do boxplot (`sns.boxplot`)
- **matplotlib.pyplot** — formatação e exibição dos gráficos

## Como Executar

1. **Criar/ativar o ambiente virtual**: `python -m venv .venv` e depois ativá-lo (na raiz do repositório)
2. **Instalar as dependências**: `pip install -r ../requirements.txt`
3. **Garantir o acesso à planilha**: copiar `../refs/Eficiencia Operacional em Linhas de Producao.xlsx` para dentro de `SPRINT_2/`, ou ajustar o caminho de leitura nos notebooks
4. **Abrir os notebooks** (Jupyter Notebook, JupyterLab, VS Code ou Google Colab)
5. **Executar cada notebook do início ao fim** ("Restart Kernel and Run All")
6. **Ordem sugerida**: `Tempo_Ciclo_Sprint2.ipynb` → `Unidades_Produzidas_Sprint2.ipynb`
7. **Conferir a execução**: ambos os notebooks devem rodar **sem nenhum erro**

## Entrega da Sprint 2

1. **2 notebooks Python**: `Tempo_Ciclo_Sprint2.ipynb` e `Unidades_Produzidas_Sprint2.ipynb`, cada um contendo quartis, boxplot, cálculo de outliers e interpretação textual dos resultados
2. Continuidade do relatório consolidado do Projeto I (seções de análise das variáveis quantitativas), a partir do documento-base "Sprint 2 - Grupo 6"

## Equipe

**Grupo 6** — Escola Politécnica, PUC-Campinas

| Nome                      | RA |
|---------------------------|-----|
| Eduarda Barbosa Kauffmann | 24004761 |
| Felipe Grolla Freitas     | 24004846 |
| Vitória Marques Pires     | 24011312 |
