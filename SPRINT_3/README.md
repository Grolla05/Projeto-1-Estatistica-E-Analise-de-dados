# Eficiência Operacional em Linhas de Produção — Projeto I / Sprint 3

Terceira e última entrega (SPRINT 3) do Projeto I da disciplina de Estatística e Análise de Dados — Escola Politécnica, PUC-Campinas. Encerra o estudo analisando a **relação entre as variáveis**: correlação e regressão linear entre as duas variáveis quantitativas (`Tempo_Ciclo_s` e `Unidades_Produzidas`) e tabulação cruzada, análise de risco e boxplot comparativo entre a variável quantitativa categorizada e a variável qualitativa (`Nivel_Automacao`). Esta sprint também compõe a **Entrega Final do Projeto I**.

## Contextualização

Nas Sprints 1 e 2, o grupo caracterizou cada variável isoladamente (tabelas de frequência, gráficos, medidas de tendência central, quartis, boxplot, outliers e dispersão). A Sprint 3 passa a investigar **como as variáveis se relacionam**, respondendo a duas perguntas:

1. **O tempo de ciclo está associado à quantidade produzida?** (correlação e regressão linear)
2. **A quantidade produzida está associada ao nível de automação da linha?** (tabulação cruzada, análise de risco e boxplot comparativo)

- **Tamanho da amostra:** 1.000 observações, mesma base de dados das sprints anteriores.
- **Variável independente (x):** `Tempo_Ciclo_s` — quanto mais longo o ciclo, menos ciclos cabem no período e, em tese, menos unidades são produzidas.
- **Variável dependente (y):** `Unidades_Produzidas`.
- **Variável categorizada:** `Unidades_Produzidas` dividida em duas categorias (baixa e alta produção) pelo critério da **mediana** (601 unidades), cruzada com `Nivel_Automacao`.

## Variáveis do Estudo

| Variável | Coluna no arquivo | Classificação | Papel na Sprint 3 |
|---|---|---|---|
| Tempo de Ciclo | `Tempo_Ciclo_s` | Quantitativa Contínua (segundos) | Variável independente (x) na regressão |
| Unidades Produzidas | `Unidades_Produzidas` | Quantitativa Discreta (contagem) | Variável dependente (y) e variável categorizada em 2 classes |
| Nível de Automação | `Nivel_Automacao` | Qualitativa Ordinal (Baixa, Média, Alta) | Variável qualitativa da tabulação cruzada e do boxplot comparativo |

## Estrutura do Projeto

```
SPRINT_3/
├── assets/
│   └── 8_Tabulação_Cruzada.ipynb      # Notebook modelo do professor (referência)
├── Correlacao_Regrssao.ipynb          # Notebook — correlação e regressão linear
├── Tabulacao_Cruzada.ipynb            # Notebook — categorização, tabulação cruzada, análise de risco e boxplot comparativo
└── README.md
```

### O que cada arquivo faz

- **`Correlacao_Regrssao.ipynb`** — Carrega a base (com `dropna()`), define x e y e justifica a escolha, constrói o **diagrama de dispersão**, calcula o **coeficiente de correlação de Pearson** com `scipy.stats.linregress`, ajusta a **reta de regressão** pelo Método dos Mínimos Quadrados, plota a reta sobre o diagrama e calcula o **coeficiente de determinação (R²)**. Cada etapa tem interpretação textual e o notebook termina com a conclusão.
- **`Tabulacao_Cruzada.ipynb`** — Categoriza `Unidades_Produzidas` em 2 classes pela mediana (com justificativa e tabela de frequências absoluta e percentual), constrói as **4 tabelas cruzadas** (frequências absolutas, percentuais do total, percentuais por linhas e por colunas) com interpretação, calcula a **razão de prevalência** (análise de risco), constrói o **boxplot comparativo** de `Unidades_Produzidas` por nível de automação e apresenta a conclusão sobre a relação entre as variáveis.
- **`assets/`** — Notebook de referência fornecido pelo professor (tabulação cruzada), usado como apoio metodológico; não faz parte da entrega.

> ⚠️ **Observação sobre o caminho dos dados:** os notebooks leem a planilha em `'../refs/Eficiencia Operacional em Linhas de Producao.xlsx'` (caminho relativo à pasta `SPRINT_3/`, apontando para a pasta `refs/` do repositório). Ao executar fora da estrutura do repositório (por exemplo, no Google Colab), copie a planilha para a mesma pasta do notebook e ajuste a leitura para `pd.read_excel('Eficiencia Operacional em Linhas de Producao.xlsx')`.

### Arquivos gerados na execução

| Arquivo | Gerado por | Descrição |
|---|---|---|
| `Eficiencia Operacional em Linhas de Producao categorizado.xlsx` | `Tabulacao_Cruzada.ipynb` | Planilha original acrescida da coluna `Producao_Categorizada` |
| `boxplot_comparativo.png` | `Tabulacao_Cruzada.ipynb` | Boxplot comparativo exportado com dpi=150 |

## Metodologia

### Correlação e regressão linear

1. **Diagrama de dispersão** de `Unidades_Produzidas` por `Tempo_Ciclo_s` para verificar a forma da relação.
2. **Coeficiente de correlação de Pearson (r)** para medir o sentido e a intensidade da relação linear.
3. **Regressão linear simples** (ŷ = a + b·x), com coeficiente linear (a), coeficiente angular (b) e **coeficiente de determinação (R²)**.

### Tabulação cruzada e análise de risco

1. **Categorização:** `Unidades_Produzidas` ≤ mediana (601) → *baixa producao*; acima → *alta producao*. A mediana divide a amostra em grupos praticamente iguais (501 e 499 linhas) e não é afetada por valores extremos.
2. **Tabelas cruzadas** entre `Producao_Categorizada` e `Nivel_Automacao`: frequências absolutas, percentuais do total, percentuais marginais por linhas e por colunas.
3. **Análise de risco (razão de prevalência):** desfecho = baixa produção; exposição = baixa automação; referência = alta automação. RP = prevalência nos expostos ÷ prevalência na referência.
4. **Boxplot comparativo** da produção por nível de automação, com medidas-resumo (`describe()`) e análise de dispersão e outliers.

## Principais Resultados

### Correlação e regressão linear

| Medida | Valor | Interpretação |
|---|---|---|
| Coeficiente de correlação (r) | **−0,777** | Correlação linear **negativa e forte** |
| p-valor | ≈ 8,8 × 10⁻²⁰³ | Associação estatisticamente significativa |
| Reta de regressão | **ŷ = 1212,19 − 13,41 · x** | Cada segundo a mais no ciclo reduz a produção em cerca de 13,41 unidades, em média |
| Coeficiente de determinação (R²) | **0,6037** | Cerca de 60,4% da variação da produção é explicada pelo tempo de ciclo |

O diagrama de dispersão forma uma nuvem descendente, aproximadamente linear, mais dispersa nos ciclos curtos (abaixo de ~40 s). O coeficiente linear (≈ 1212,19) é uma extrapolação sem sentido prático, pois o menor tempo de ciclo observado é ~24,8 s.

### Tabulação cruzada

Frequências absolutas (`Producao_Categorizada` × `Nivel_Automacao`):

| | Baixa | Média | Alta | Total |
|---|---|---|---|---|
| **baixa producao** | 143 | 230 | 128 | 501 |
| **alta producao** | 61 | 235 | 203 | 499 |
| **Total** | 204 | 465 | 331 | 1000 |

Proporção de linhas com **alta produção** em cada nível de automação (percentuais por colunas): **29,9%** (Baixa), **50,5%** (Média) e **61,3%** (Alta). Apenas 6,1% das linhas combinam baixa automação com alta produção, contra 20,3% que combinam alta automação com alta produção.

### Análise de risco

| Grupo | Linhas com baixa produção | Total de linhas | Prevalência |
|---|---|---|---|
| Exposto (baixa automação) | 143 | 204 | 70,10% |
| Referência (alta automação) | 128 | 331 | 38,67% |

**Razão de prevalência (RP) ≈ 1,81:** a prevalência de baixa produção nas linhas de baixa automação é cerca de 1,81 vezes (81% maior) a das linhas de alta automação. Como RP > 1, a baixa automação está associada a maior prevalência de baixa produção. Trata-se de uma associação observada nos dados, não de prova de causalidade.

### Boxplot comparativo

| Nível de automação | n | Média | Mediana | Q1–Q3 | Desvio padrão | Outliers |
|---|---|---|---|---|---|---|
| Baixa | 204 | 539,64 | 524,5 | 436–628,5 | 135,21 | 3 |
| Média | 465 | 618,09 | 606,0 | 502–724 | 158,94 | 1 |
| Alta | 331 | 677,33 | 647,0 | 546–802,5 | 185,50 | 2 |

A produção típica cresce com o nível de automação, mas as caixas se sobrepõem parcialmente: a automação aumenta a produção, sem separar totalmente os grupos. A dispersão cresce com a automação, com coeficientes de variação parecidos (25,1%; 25,7%; 27,4%). Todos os outliers estão acima do limite superior.

## Conclusão da Sprint

As análises apontam no mesmo sentido: **ciclos mais curtos e maior automação estão associados a maior produção**. O tempo de ciclo explica cerca de 60% da variação da produção, e o nível de automação ajuda a explicar parte do restante. Como as distribuições se sobrepõem, a automação não é o único fator relevante.

## Base de Dados

Mesma base das sprints anteriores — [`../refs/Eficiencia Operacional em Linhas de Producao.xlsx`](../refs) — 1.000 linhas × 3 colunas (`Nivel_Automacao`, `Tempo_Ciclo_s`, `Unidades_Produzidas`).

## Tecnologias e Bibliotecas Utilizadas

[![My Skills](https://skillicons.dev/icons?i=python,pycharm)](https://skillicons.dev)

- **pandas** — leitura da planilha, tabelas de frequência, tabelas cruzadas (`pd.crosstab`) e medidas-resumo
- **math** — apoio a cálculos numéricos
- **scipy** (`scipy.stats.linregress`) — correlação de Pearson, reta de regressão e p-valor
- **seaborn** — boxplot comparativo (`sns.boxplot`)
- **matplotlib.pyplot** — diagrama de dispersão, reta de regressão e formatação dos gráficos
- **openpyxl** — leitura e escrita de arquivos `.xlsx` via `pandas`

## Como Executar

1. **Criar/ativar o ambiente virtual**: `python -m venv .venv` e depois ativá-lo (na raiz do repositório)
2. **Instalar as dependências**: `pip install -r ../requirements.txt`
3. **Garantir o acesso à planilha**: manter a estrutura do repositório (`../refs/`) ou ajustar o caminho de leitura nos notebooks
4. **Abrir os notebooks** (Jupyter Notebook, JupyterLab, VS Code ou Google Colab)
5. **Executar cada notebook do início ao fim** ("Restart Kernel and Run All")
6. **Ordem sugerida**: `Correlacao_Regrssao.ipynb` → `Tabulacao_Cruzada.ipynb`
7. **Conferir a execução**: ambos os notebooks devem rodar **sem nenhum erro**

## Entrega da Sprint 3

1. **2 notebooks Python**: `Correlacao_Regrssao.ipynb` e `Tabulacao_Cruzada.ipynb`, com interpretação textual dos resultados
2. **1 planilha Excel**: base de dados do projeto (e a versão categorizada, gerada pelo notebook de tabulação cruzada)
3. **1 arquivo PDF**: relatório consolidado do Projeto I, com capa, introdução, análise de cada variável, análise de relações (boxplot comparativo, correlação e regressão, tabelas cruzadas e análise de risco) e conclusão/considerações finais
4. **Notebooks das Sprints 1 e 2**, atualizados com as correções, quando houver

## Equipe

**Grupo 6** — Escola Politécnica, PUC-Campinas

| Nome                      | RA |
|---------------------------|-----|
| Eduarda Barbosa Kauffmann | 24004761 |
| Felipe Grolla Freitas     | 24004846 |
| Vitória Marques Pires     | 24011312 |