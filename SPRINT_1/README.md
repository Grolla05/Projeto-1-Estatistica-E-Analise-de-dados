# Eficiência Operacional em Linhas de Produção — Projeto I / Sprint 1

Estudo estatístico descritivo sobre a eficiência operacional de linhas de produção industrial, relacionando o **nível de automação** das linhas com o **tempo de ciclo** e a **quantidade de unidades produzidas**. O trabalho é a primeira entrega (SPRINT 1) do Projeto I da disciplina de Estatística e Análise de Dados — Escola Politécnica, PUC-Campinas — contemplando tabelas de frequência, representações gráficas e medidas de tendência central (média, moda e mediana) para as três variáveis selecionadas.

## Contextualização e Problematização

Em ambientes industriais, o nível de automação de uma linha de produção é frequentemente apontado como um dos principais fatores de ganho de eficiência, impactando diretamente o tempo necessário para completar um ciclo produtivo e o volume de unidades entregues em um determinado período. Este projeto busca **investigar, de forma descritiva, se e como o nível de automação (Baixa, Média, Alta) se relaciona com o tempo de ciclo (em segundos) e com a quantidade de unidades produzidas**, utilizando técnicas de estatística descritiva (tabelas de frequência, gráficos e medidas de tendência central).

- **Problematização:** existe indício, a partir da distribuição dos dados, de que linhas com maior nível de automação apresentam tempos de ciclo menores e/ou maior volume de unidades produzidas?
- **Objetivo:** organizar, resumir e visualizar os dados de 1.000 registros de linhas de produção para caracterizar o comportamento das três variáveis do estudo e apoiar, em sprints futuras, uma análise de correlação/dependência entre as variáveis quantitativas.
- **Tamanho da amostra:** 1.000 observações (linhas do arquivo de dados).

## Variáveis do Estudo

| Variável | Coluna no arquivo | Classificação | Notebook final |
|---|---|---|---|
| Nível de Automação | `Nivel_Automacao` | Qualitativa Ordinal (Baixa, Média, Alta) | [`Nivel_Automacao.ipynb`](Nivel_Automacao.ipynb) |
| Tempo de Ciclo | `Tempo_Ciclo_s` | Quantitativa Contínua (segundos, valores decimais) — organizada em **classes** | [`Tempo_ciclo.ipynb`](Tempo_ciclo.ipynb) |
| Unidades Produzidas | `Unidades_Produzidas` | Quantitativa Discreta (contagem, número inteiro) — organizada em **classes** | [`Unidades_Produzidas.ipynb`](Unidades_Produzidas.ipynb) |

A escolha das duas variáveis quantitativas (`Tempo_Ciclo_s` e `Unidades_Produzidas`) visa investigar, em etapas futuras do Projeto I, uma possível **relação de dependência/correlação** entre elas — é esperado que ciclos mais curtos estejam associados a maior volume de unidades produzidas — tendo o `Nivel_Automacao` como variável categórica de segmentação da análise.

## Estrutura do Projeto

Cada variável do estudo tem **um único notebook final**, autocontido, com tabela de frequências, gráfico e medidas de tendência central (média/moda/mediana) já interpretadas — reunindo em um só arquivo o que os templates de referência do professor apresentam separados em "tabela" e "gráficos e medidas".

```
Projeto-1-SPRINT-1/
├── Assets/
│   ├── 1_Tab_varquali.ipynb
│   ├── 2_Tab_vardiscreta.ipynb
│   ├── 3_Tab_varcontinua_classes.ipynb
│   └── 4_Gráficos_e_medidas.ipynb
├── refs/                                                   # Material de referência do professor (NÃO versionado, exceto dados/README)
│   └── Eficiencia Operacional em Linhas de Producao.xlsx   # Base de dados do projeto
├── .gitignore
├── Nivel_Automacao.ipynb                                   # Notebook — variável qualitativa
├── Tempo_ciclo.ipynb                                       # Notebook — variável quantitativa contínua
├── Unidades_Produzidas.ipynb                               # Notebook — variável quantitativa discreta
├── requirements.txt                                        # Dependências do projeto
└── README.md
```

### O que cada arquivo faz

- **`Nivel_Automacao.ipynb`** — Lê a base de dados, monta a tabela de distribuição de frequências (absoluta e relativa) da variável `Nivel_Automacao` respeitando a ordem natural da escala (Baixa → Média → Alta), constrói gráfico de colunas e gráfico de setor, calcula a moda e interpreta o resultado.
- **`Tempo_ciclo.ipynb`** — Lê a base de dados, define os limites de classe para `Tempo_Ciclo_s`, monta a tabela de distribuição de frequências por classes (absoluta, relativa, acumulada e relativa acumulada), constrói o histograma e calcula/interpreta média, mediana, moda e classe modal.
- **`Unidades_Produzidas.ipynb`** — Lê a base de dados, define os limites de classe para `Unidades_Produzidas`, monta a tabela de distribuição de frequências por classes (absoluta, relativa, acumulada e relativa acumulada), constrói o histograma e calcula/interpreta média, mediana, moda e classe modal.
- **`../requirements.txt`** — Lista as bibliotecas Python necessárias para rodar os notebooks (pandas, numpy, matplotlib, seaborn, openpyxl).
- **`../.gitignore`** — Garante que `../.venv` e os notebooks de referência dentro de `refs` não sejam versionados no GitHub.
- **`refs`** — Pasta de apoio com o material original fornecido pelo professor:
  - `1_Tab_varquali.ipynb`, `2_Tab_vardiscreta.ipynb`, `3_Tab_varcontinua_classes.ipynb`, `4_Gráficos_e_medidas.ipynb`: notebooks **modelo**, usados como referência de sintaxe/metodologia durante o desenvolvimento, mas **não fazem parte da entrega** e não sobem para o GitHub.
  - `Eficiencia Operacional em Linhas de Producao.xlsx`: base de dados real do grupo, utilizada pelos notebooks finais na raiz.
  - `README.md`: anotações internas sobre como os templates foram usados de referência.

> ⚠️ **Observação:** os arquivos dentro de `../refs/1_*.ipynb` a `../refs/4_*.ipynb` usam, originalmente, uma base de exemplo genérica do professor (`dados_projeto1.xlsx`, com colunas como `Escolaridade`, `Idade`, `Sexo`). Eles servem **apenas como referência de metodologia** (como montar tabela de frequência, classes, gráficos e medidas) — a lógica foi adaptada nos notebooks finais da raiz para usar a base real do grupo (`Eficiencia Operacional em Linhas de Producao.xlsx`) e as colunas `Nivel_Automacao`, `Tempo_Ciclo_s` e `Unidades_Produzidas`.

## Base de Dados

**Localização:** [`refs/Eficiencia Operacional em Linhas de Producao.xlsx`](refsficiencia Operacional em Linhas de Producao.xlsx) — utilizada como fonte de dados pelos três notebooks finais na raiz do projeto.

- **Planilha:** `Dados`
- **Dimensões:** 1.000 linhas × 3 colunas
- **Colunas:**

| Coluna | Tipo | Descrição |
|---|---|---|
| `Nivel_Automacao` | Texto (categórico) | Nível de automação da linha de produção |
| `Tempo_Ciclo_s` | Numérico decimal | Tempo de ciclo produtivo, em segundos |
| `Unidades_Produzidas` | Numérico inteiro | Quantidade de unidades produzidas |

**Distribuição da variável qualitativa (`Nivel_Automacao`):** Média, Alta, Baixa.

> 💡 Como os notebooks finais ficam na **raiz** do projeto e a planilha está dentro de `refs`, a leitura dos dados deve apontar para o caminho relativo, por exemplo: `pd.read_excel('refs/Eficiencia Operacional em Linhas de Producao.xlsx')`.

## Tecnologias e Bibliotecas Utilizadas

[![My Skills](https://skillicons.dev/icons?i=python,pycharm)](https://skillicons.dev)

Manipulação de tabelas e criação de gráficos:

- **pandas** — leitura da planilha (`.xlsx`) e manipulação/agrupamento dos dados
- **math** — apoio a cálculos estatísticos
- **numpy** — cálculo de frequências acumuladas e apoio às classes de intervalo
- **seaborn** — gráficos de contagem (`countplot`) e histogramas
- **matplotlib.pyplot** — construção e formatação de gráficos (barras, pizza, histograma)

## Como Executar

1. **Criar/ativar o ambiente virtual**: `python -m venv .venv` e depois ativá-lo
2. **Instalar as dependências**: `pip install -r requirements.txt`
3. **Abrir os notebooks** (Jupyter Notebook, JupyterLab, VS Code ou Google Colab)
4. **Executar cada notebook do início ao fim** ("Restart Kernel and Run All"), garantindo que o caminho de leitura da planilha aponte para `refs/Eficiencia Operacional em Linhas de Producao.xlsx`
5. **Ordem sugerida**: `Nivel_Automacao.ipynb` → `Tempo_ciclo.ipynb` → `Unidades_Produzidas.ipynb`
6. **Conferir a execução**: todos os notebooks devem rodar **sem nenhum erro**, conforme exigido na rubrica de avaliação

## Entrega da Sprint 1

1. **3 notebooks Python**: `Nivel_Automacao.ipynb`, `Tempo_ciclo.ipynb` e `Unidades_Produzidas.ipynb`
2. **1 planilha Excel**: `Eficiencia Operacional em Linhas de Producao.xlsx`
3. **1 arquivo PDF final**, contendo:
   - Capa com: Escola, Faculdade, nome da disciplina, nome e RA dos integrantes do grupo, mês/ano
   - Contextualização do problema, objetivo e justificativa das variáveis
   - Prints das telas dos notebooks (opcional) **sempre acompanhados de interpretação/comentários** — não são aceitos apenas prints sem texto explicativo

O envio dos arquivos é pré-requisito para a correção pela rubrica de avaliação (10 pontos), distribuídos entre: definição do problema, tabelas de frequência e gráficos de cada variável, medidas resumo (média, moda, mediana) de cada variável, qualidade dos notebooks/planilha e qualidade geral da entrega em PDF.

## Equipe

**Grupo 6** — Escola Politécnica, PUC-Campinas

| Nome                      |
|---------------------------|
| Eduarda Barbosa Kauffmann |
| Felipe Grolla Freitas     |
| Vitória Marques Pires     |
