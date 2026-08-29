# 📦 Olist E-Commerce — Análise de Performance Comercial

Projeto de portfólio com fluxo completo de dados: carregamento → limpeza com Python → banco SQLite → consultas SQL → exportação para Power BI.

---

## 🎯 Contexto e Objetivo

O dataset público da Olist contém informações reais de um e-commerce brasileiro com mais de 100 mil pedidos entre 2016 e 2018. O objetivo deste projeto é simular o trabalho de um Analista de BI: transformar dados brutos em um painel interativo que responda perguntas estratégicas de negócio.

**Perguntas respondidas:**
- Quantos pedidos foram feitos e qual foi a receita total?
- Qual é a média de avaliação dos clientes?
- Quais são os meses com mais vendas?
- Quais estados compram mais?
- Qual é a taxa de atraso nas entregas?

---

## 🛠️ Tecnologias Utilizadas

| Etapa | Ferramenta |
|-------|-----------|
| Limpeza e transformação | Python (Pandas) |
| Banco de dados relacional | SQLite |
| Consultas analíticas | SQL |
| Visualização | Power BI |
| Versionamento | Git + GitHub |

---

## 📁 Estrutura do Repositório

```
olist-bi-dashboard/
├── data/
│   ├── raw/                        ← arquivos originais do Kaggle (não versionados)
│   └── processed/                  ← tabelas limpas exportadas para o Power BI
├── notebooks/
│   └── olist_analise_junior.ipynb  ← análise completa: ETL + SQL
├── dashboard/
│   └── olist_dashboard.pbix        ← arquivo Power BI
├── .gitignore
└── README.md
```

---

## ▶️ Como Executar

**1. Clone o repositório**
```bash
git clone https://github.com/Camilarmota/olist-bi-dashboard.git
cd olist-bi-dashboard
```

**2. Instale as dependências**
```bash
pip install pandas ipykernel
```

**3. Baixe o dataset**

Acesse o Kaggle e baixe o [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).  
Extraia os arquivos abaixo na pasta `data/raw/`:

```
olist_orders_dataset.csv
olist_order_items_dataset.csv
olist_order_reviews_dataset.csv
olist_customers_dataset.csv
```

**4. Execute o notebook**
```bash
jupyter notebook notebooks/olist_analise_junior.ipynb
```
Clique em **Run All**. Os arquivos processados serão gerados automaticamente em `data/processed/`.

**5. Abra o dashboard**

No Power BI Desktop, abra `dashboard/olist_dashboard.pbix`.  
Se necessário, atualize o caminho dos arquivos em *Transformar Dados → Configurações da Fonte*.

---

## 📊 O que o Notebook Faz

| Seção | Descrição |
|-------|-----------|
| 1. Imports | Carrega as bibliotecas necessárias |
| 2. Carregamento | Lê os 4 CSVs do Kaggle |
| 3. Primeiro olhar | Explora colunas, tipos e valores nulos |
| 4. Limpeza | Converte datas, calcula tempo de entrega e flag de atraso |
| 5. KPIs | Calcula receita, ticket médio, nota média e taxa de atraso |
| 6. Banco SQLite | Salva os dados limpos em um banco relacional local |
| 7. Consultas SQL | Responde as perguntas de negócio com SQL |
| 8. Exportação | Salva os resultados em CSV para o Power BI |
| 9. Conclusões | Resumo dos principais insights encontrados |

---

## 📊 Páginas do Dashboard (Power BI)

**Página 1 — Visão Geral**  
KPIs de receita total, pedidos, nota média e taxa de atraso. Evolução mensal de vendas.

**Página 2 — Entregas por Estado**  
Mapa de pedidos por estado e ranking de atrasos por região.

**Página 3 — Satisfação do Cliente**  
Distribuição de notas e correlação entre atraso e avaliação.

---

## 💡 Principais Insights

> *Valores preenchidos após execução do notebook.*

- 📈 **Sazonalidade:** pico de vendas em novembro (Black Friday)
- 🚚 **Logística:** estados do Norte e Nordeste concentram as maiores taxas de atraso
- ⭐ **Satisfação:** pedidos atrasados tendem a receber notas mais baixas
- 🛍️ **Receita:** SP, RJ e MG concentram a maior parte dos pedidos

---

## 👩‍💻 Sobre a Autora

**Camila Rodrigues Mota**  
Analista de Dados & BI Júnior | Salvador, BA

Profissional em transição de carreira da área da saúde para Dados e BI, com experiência em Python, SQL e Power BI.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Camila%20Mota-0077B5?style=flat&logo=linkedin)](https://linkedin.com/in/camila-rodrigues-mota/)
[![GitHub](https://img.shields.io/badge/GitHub-Camilarmota-181717?style=flat&logo=github)](https://github.com/Camilarmota)

---

*Dataset público disponibilizado pela [Olist](https://olist.com) via Kaggle sob licença CC BY-NC-SA 4.0.*
