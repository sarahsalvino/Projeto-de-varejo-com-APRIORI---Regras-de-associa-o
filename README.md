🛒 Análise de Regras de Associação — Varejo Brasil

Descobrindo padrões de comportamento de compra em 9.835 transações de varejo brasileiro com o algoritmo Apriori.


📌 Objetivo
Identificar quais produtos são comprados juntos com frequência, revelando padrões ocultos no comportamento dos consumidores. O resultado prático são regras de associação acionáveis — inteligência direta para estratégias de cross-selling, layout de loja e campanhas promocionais.

🗂️ Sobre os Dados
AtributoDetalheBasevarejo_brasil_long.csvTotal de transações9.835FormatoLong format — cada linha representa um item de uma transaçãoColunas principaistransacao_id, item

🔄 Fluxo do Projeto
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

⚙️ Parâmetros do Modelo
ParâmetroValorInterpretaçãoSuporte mínimo0.005~50 transações mínimasConfiança mínima0.5050% de probabilidade condicionalFiltro de Lift> 1Apenas associações genuínas

📊 Resultados
EtapaResultadoPadrões frequentes encontrados3.133Regras com Lift > 1234Lift máximo encontrado15.66
🏆 Top 10 Regras por Lift
AntecedenteConsequenteConfiançaLiftlegumes congelados + batata congeladafrango congelado89,14%15.66frango congelado + legumes congeladosbatata congelada85,25%15.38papel higiênico + detergenteproduto de limpeza52,60%12.65produto de limpeza + detergentepapel higiênico92,04%12.02chantilly + chocolateleite condensado82,51%11.26fermento em pó + outros legumes + manteigafarinha de trigo86,67%10.14

💡 Principais Insights
1. Interdependência de Categorias — Congelados
A combinação legumes congelados + batata congelada → frango congelado atingiu Lift de 15.66, provando que esses itens são comprados como uma solução completa de refeição, não de forma isolada. Clientes que levam dois desses produtos têm ~15x mais chance de levar o terceiro.
2. Abastecimento Logístico — Higiene e Limpeza
Regras envolvendo produto de limpeza, detergente e papel higiênico aparecem repetidamente com altíssima confiança (até 92%). Quando o cliente decide abastecer a área de serviço, tende a levar a categoria inteira.
3. Gatilhos de Indulgência — Sobremesas
Chantilly + chocolate → leite condensado (Lift 11.26) revela um padrão claro de compras voltadas a momentos de sobremesa e indulgência — ideal para ações promocionais sazonais.

🧰 Tecnologias Utilizadas

Python 3
Pandas — manipulação e exploração dos dados
Matplotlib / Seaborn — visualizações
mlxtend — algoritmo Apriori e geração de regras de associação (TransactionEncoder, apriori, association_rules)
