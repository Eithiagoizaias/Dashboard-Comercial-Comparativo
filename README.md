# 📊 Melhoria Operacional — Devoluções e Defeitos | 1º Semestre 2025 vs 2026
 
Dashboard desenvolvido no Power BI para análise comparativa de devoluções e defeitos de produtos entre o 1º Semestre de 2025 e o 1º Semestre de 2026, com foco em evidenciar a melhoria operacional para o Setor Comercial.
 
![Dashboard Preview](Vale_Troca_comparativo_1semestre_2025_2026.png)
 
---
 
## 📈 Resultados
 
| Métrica | 1S 2025 | 1S 2026 | Variação |
|---|---|---|---|
| Total de Trocas | 318 | 65 | **-80%** |
| Valor Financeiro | R$ 21.350,00 | R$ 6.180,00 | **-71%** |
 
---
 
## 🗂️ Arquivos
 
| Arquivo | Descrição |
|---|---|
| `vale_comparativo.pbix` | Arquivo Power BI com o dashboard completo |
| `VALE_TROCA_ATK_SJM.xlsx` | Base de dados original com os registros de vale troca |
| `Vale_Troca_comparativo_1semestre_2025_2026.png` | Print do dashboard final |
 
---
 
## 🛠️ Etapas do Projeto
 
### 1. Power Query — Limpeza e Transformação
- Remoção de linhas de cabeçalho e rodapé desnecessárias
- Correção de tipos de dados (datas, valores numéricos)
- Adição da coluna `Ano Origem` via coluna personalizada (`Date.Year`)
- Consolidação das 3 tabelas anuais em uma única tabela `Trocas` via **Append (Acrescentar Consultas)**
- Desativação do carregamento das tabelas originais para manter o modelo limpo
### 2. Modelagem
- Criação de tabela `Calendario` com DAX (`CALENDAR` + `ADDCOLUMNS`)
- Colunas calculadas: `Ano`, `Mes`, `NomeMes`, `Semestre`, `AnoMes`
- Relacionamento entre `Calendario[Date]` e `Trocas[DATA DA TROCA]` (1 para muitos)
### 3. Medidas DAX
```dax
-- Totais por semestre
Total Valor 2025 1S = CALCULATE([Total Valor], Calendario[Ano]=2025, Calendario[Semestre]="1º Semestre")
Total Valor 2026 1S = CALCULATE([Total Valor], Calendario[Ano]=2026, Calendario[Semestre]="1º Semestre")
 
-- Variação percentual
Variacao % Valor 1S = DIVIDE([Total Valor 2026 1S] - [Total Valor 2025 1S], [Total Valor 2025 1S])
Variacao % Qtd Trocas 1S = DIVIDE([Qtd Trocas 2026 1S] - [Qtd Trocas 2025 1S], [Qtd Trocas 2025 1S])
 
-- Ticket médio
Ticket Medio 2025 1S = CALCULATE([Ticket Medio], Calendario[Ano]=2025, Calendario[Semestre]="1º Semestre")
Ticket Medio 2026 1S = CALCULATE([Ticket Medio], Calendario[Ano]=2026, Calendario[Semestre]="1º Semestre")
```
 
### 4. Decisão Metodológica
A comparação foi limitada ao **1º Semestre em ambos os anos** (jan–jun) para garantir uma análise justa. Comparar o ano completo de 2025 com um 2026 ainda em curso distorceria os resultados — a melhoria observada é real, não é artefato do período incompleto.
 
---
 
## 📐 Estrutura do Dashboard
 
- **KPIs** — Valor total e quantidade de trocas por ano, com variação percentual em destaque (verde)
- **Gráfico de Colunas Comparativo** — Valor mensal de devoluções lado a lado (2025 vs 2026)
---
 
## 🧰 Tecnologias
 
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
 
---
 
## 👤 Autor
 
**Thiago Izaias**  
[LinkedIn](https://linkedin.com/in/eithiagoizaias) • [Portfólio](https://eithiagoizaias.vercel.app) • [GitHub](https://github.com/Eithiagoizaias)
