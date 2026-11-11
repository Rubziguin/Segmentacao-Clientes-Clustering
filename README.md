# Segmentação de clientes com clusterização

Mini projeto de **IA não supervisionada (clusterização)**.

**Dupla**
- Rubens Rodrigues Maranesi — RA00331129
- Pedro Gabriel Takenobu Serafim — RA00340890

## Sobre o projeto

Usamos dados de 2.240 clientes de uma rede de supermercados para descobrir quais perfis de cliente existem na base e como cada perfil deveria ser abordado pelo marketing.

O notebook [`segmentacao_clientes.ipynb`](segmentacao_clientes.ipynb) contém:

1. Análise exploratória e limpeza (valores faltantes, idades impossíveis, renda inválida, categorias inconsistentes)
2. Engenharia de features (gasto total, nº de filhos, total de compras, tempo de casa)
3. Pré-processamento com `StandardScaler`
4. K-Means, com escolha de `k` por cotovelo, silhouette, Davies-Bouldin e teste de estabilidade
5. Comparação com Affinity Propagation e agrupamento hierárquico (Ward)
6. Visualização dos clusters com PCA
7. Interpretação dos segmentos (mix de produtos, canais de compra, resposta às campanhas e perfil demográfico), conclusões e limitações

## Dataset

[Customer Personality Analysis](https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis) (Kaggle): 2.240 clientes e 29 colunas com dados demográficos, gastos por categoria de produto, compras por canal e resposta a 6 campanhas de marketing. O arquivo está em `data/` e é separado por tabulação.

## Principais resultados

Depois da limpeza ficaram 2.212 clientes, agrupados com K-Means (k = 4):

| Segmento | Clientes | Renda média | Gasto médio (2 anos) | % do faturamento | Aceitou a última campanha |
|---|---|---|---|---|---|
| Premium | 668 | 75 mil | 1.278 | 64% | 25% |
| Famílias caçadoras de promoção | 472 | 57 mil | 776 | 27% | 15% |
| Famílias maiores, gasto baixo | 464 | 42 mil | 124 | 4% | 6% |
| Jovens de renda baixa | 608 | 30 mil | 108 | 5% | 11% |

- Renda e número de filhos são os fatores que mais separam os clientes.
- Os segmentos também diferem em variáveis que não entraram no modelo (mix de produtos, canal de compra e resposta às campanhas).
- O silhouette é moderado (cerca de 0,26): os clientes formam um contínuo, e os segmentos são faixas desse contínuo.

## Como executar

```bash
pip install -r requirements.txt
jupyter notebook segmentacao_clientes.ipynb
```

## Estrutura

```
├── segmentacao_clientes.ipynb
├── data/
│   └── marketing_campaign.csv
├── requirements.txt
└── README.md
```
