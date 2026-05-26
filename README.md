# 🛒 Análise de Regras de Associação — Varejo Brasil

> Descobrindo padrões de comportamento de compra em 9.835 transações de varejo brasileiro com o algoritmo **Apriori**.

---

## 📌 Objetivo

Identificar quais produtos são comprados juntos com frequência, revelando padrões ocultos no comportamento dos consumidores. O resultado prático são **regras de associação acionáveis** — inteligência direta para estratégias de cross-selling, layout de loja e campanhas promocionais.

---

## 🗂️ Sobre os Dados

| Atributo | Detalhe |
|---|---|
| **Base** | `varejo_brasil_long.csv` |
| **Total de transações** | 9.835 |
| **Formato** | Long format — cada linha representa um item de uma transação |
| **Colunas principais** | `transacao_id`, `item` |

---

## 🔄 Fluxo do Projeto

```
Dados brutos (long format)  
        ↓  
Análise Exploratória (EDA)  
        ↓  
Agrupamento por transação → lista de listas  
        ↓  
Codificação booleana (TransactionEncoder)  
        ↓  
Algoritmo Apriori → padrões frequentes  
        ↓  
Geração de Regras de Associação  
        ↓  
Filtro por Lift > 1 → regras genuínas  
        ↓  
Visualização e Conclusão  
```

---

## ⚙️ Parâmetros do Modelo

| Parâmetro | Valor | Interpretação |
|---|---|---|
| **Suporte mínimo** | 0.005 | ~50 transações mínimas |
| **Confiança mínima** | 0.50 | 50% de probabilidade condicional |
| **Filtro de Lift** | > 1 | Apenas associações genuínas |

---

## 📊 Resultados

| Etapa | Resultado |
|---|---|
| Padrões frequentes encontrados | **3.133** |
| Regras com Lift > 1 | **234** |
| Lift máximo encontrado | **15.66** |

### 🏆 Top 10 Regras por Lift

| Antecedente | Consequente | Confiança | Lift |
|---|---|---|---|
| legumes congelados + batata congelada | frango congelado | 89,14% | 15.66 |
| frango congelado + legumes congelados | batata congelada | 85,25% | 15.38 |
| papel higiênico + detergente | produto de limpeza | 52,60% | 12.65 |
| produto de limpeza + detergente | papel higiênico | 92,04% | 12.02 |
| chantilly + chocolate | leite condensado | 82,51% | 11.26 |
| fermento em pó + outros legumes + manteiga | farinha de trigo | 86,67% | 10.14 |

<img width="1183" height="583" alt="output" src="https://github.com/user-attachments/assets/46440de2-bb95-47e8-aeaf-79bfc49ec0f4" />

---

## 💡 Principais Insights

**1. Interdependência de Categorias — Congelados**
A combinação `legumes congelados + batata congelada → frango congelado` atingiu Lift de **15.66**, provando que esses itens são comprados como uma solução completa de refeição, não de forma isolada. Clientes que levam dois desses produtos têm ~15x mais chance de levar o terceiro.

**2. Abastecimento Logístico — Higiene e Limpeza**
Regras envolvendo `produto de limpeza`, `detergente` e `papel higiênico` aparecem repetidamente com altíssima confiança (até 92%). Quando o cliente decide abastecer a área de serviço, tende a levar a categoria inteira.

**3. Gatilhos de Indulgência — Sobremesas**
`Chantilly + chocolate → leite condensado` (Lift 11.26) revela um padrão claro de compras voltadas a momentos de sobremesa e indulgência — ideal para ações promocionais sazonais.

---

## 🧰 Tecnologias Utilizadas

- **Python**
- **Pandas** — manipulação e exploração dos dados
- **Matplotlib / Seaborn** — visualizações
- **mlxtend** — algoritmo Apriori e geração de regras de associação (`TransactionEncoder`, `apriori`, `association_rules`)

---
