# 🛡️ Insurance Risk Intelligence Project — Claims & Risk Analytics

Este repositório contém o projeto de análise avançada e inteligência de risco para o setor de seguros de automóveis (Auto Insurance). O objetivo principal é estruturar dados transacionais de subscrição e sinistros para mitigar perdas operacionais, identificar padrões de fraudes e otimizar o portfólio de apólices.

---

## 📊 Resumo Executivo & KPIs Chave

* **Volume Total de Apólices:** 20.000 apólices modeladas
* **Prêmio Comercial Arrecadado:** R$ 85,4 Mi
* **Total em Indenizações Pagas:** R$ 14,3 Mi
* **Taxa Global de Sinistralidade:** **16,76%** (Índice saudável)
* **Mapeamento de Anomalias/Fraudes:** **174 casos** mapeados para auditoria (0,87% da base)

---

## 🗺️ Análise de Risco por Região Geográfica

| Região | Índice de Sinistralidade | Perfil de Risco |
| :--- | :---: | :--- |
| **Sudeste** | `21,59%` | Alta concentração e maior volume indenizatório |
| **Norte** | `18,23%` | Severidade moderada/alta |
| **Sul & Centro-Oeste** | `< 8,50%` | Carteiras altamente rentáveis e equilibradas |

---

## 🛠️ Tecnologias e Ferramentas Utilizadas

* **Power BI & DAX:** Modelagem dimensional e criação de métricas dinâmicas.
* **SQL Server / DuckDB:** Tratamento, higienização e consultas agregadas.
* **Python (Pandas / Jupyter):** Análise exploratória e validação de consistência dos dados.
* **HTML/CSS:** Estruturação dos painéis e componentes visuais de apresentação.

---

## 🧮 Principais Medidas em DAX Implementadas

```dax
// Total de Prêmios Comerciais Arrecadados
Total_Premio_Comercial = SUM(Fatos_Apolices[Valor_Premio])

// Total de Indenizações por Sinistro
Total_Valor_Sinistros = SUM(Fatos_Sinistros[Valor_Indenizacao])

// Taxa de Sinistralidade (%)
Taxa_Sinistralidade = 
DIVIDE(
    [Total_Valor_Sinistros],
    [Total_Premio_Comercial],
    0
)

// Mapeamento de Suspeitas de Fraude
Total_Casos_Fraude = 
CALCULATE(
    COUNTROWS(Fatos_Sinistros),
    Fatos_Sinistros[Indicador_Suspeita_Fraude] = 1
)


