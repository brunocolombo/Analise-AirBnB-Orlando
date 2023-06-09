# AirBnB_Orlando
# Análise de Dados do AirBnB de Orlando

## Contexto do Projeto
Análisar dados do AirBnB da cidade de Orlando na Flórida, com o objetivo de encontrar os melhores tipos de propriedades para investimentos.

Os dados utilizados nesse projeto foram do arquivo OrlandoAirbnbRental.xlsx que possui tabs com dados de mercado de 635 propriedades, como Receita mensal, Taxa de Ocupação mensal, custos para se manter uma propriedade, benchmarks de mercado, preço médio do aluguel, entre outros. 

## Ferramentas Utilizadas no Projeto
- Google Sheets
- SQL
- Tableau
- Google Slides

## Perguntas feitas
Com o intuito de identificar os melhores tipos de propriedades, algumas perguntas foram desenvolvidas.

**1 - Existe seasonalidade na Receita e/ou taxa de ocupação?**

**2 - Qual a diferença na Receita por número de quartos?**

**3 - Qual a taxa de ocupação por número de quartos?**

**4 - É possível que um melhor Rating na plataforma se reflita num maior preço médio?**

**5 - Qual o melhor tipo de propriedade para se investir?**

## Propriedades para Investimentos.
Também incluso nos dados haviam 8 propriedades que estão a venda, analisaremos, se é rentavél a compra de alguma dessas propriedades, por meio de cáculos utilizando receita esperada, gastos com a propriedade, entra + parcelas mensais(para a compra da propriedade), e cenário de baixa no mercado de aluguéis.
 
![investment_properties_orlando](https://user-images.githubusercontent.com/77849519/232916925-ce3b3442-0fb3-499f-92da-416777b33bd2.png)


## Explorando e Transformando dados utilizando linguagem SQL
### 1. Unpivot da Tabela Receita Mensal
* Como a tabela estava em sentido horizontal, com cada mês sendo uma coluna, nós faremos o unpivot da mesma, para poder utilizada de maneira mais eficiente depois na visualização dos dados.

```sql
SELECT id, bedrooms, MONTH, revenue 
FROM
(SELECT id, bedrooms, january, february, march, april, may, june, july, august,
september, october, november, december
FROM monthly_reveneu) t1
UNPIVOT
(revenue FOR MONTH IN (january, february, march, april, may, june, july, august,
september, october, november, december));
```
<img src="https://user-images.githubusercontent.com/77849519/232918502-3eb3d937-c69b-4a3b-a2f7-0b27073a47df.png" width="70%">

### 2. Unpivot da Tabela Taxa de Ocupação Mensal
* A tabela se encontra no sentido horizontal do mesmo modo da tabela Receita Mensal, então faremos o mesmo processo de unpivot.
```sql
SELECT id, bedrooms, MONTH, occupacy_rate 
FROM
(SELECT id, bedrooms, january, february, march, april, may, june, july, august,
september, october, november, december
FROM ocupacao_calendario) t1
UNPIVOT
(occupacy_rate FOR MONTH IN (january, february, march, april, may, june, july, august,
september, october, november, december));
```
<img src="https://user-images.githubusercontent.com/77849519/232919306-20e8ec92-0792-4740-bbab-2085f3e7556f.png" width="70%">

## Gráficos
Os Gráficos foram criados a partir das tabelas 'Receita Mensal', 'Ocupação mensal', 'Airbnb_listings_orlando', 'Investment_properties' utilizando o **Tableau**.

## Apresentação da Análise
No arquivo em PDF a seguir se encontra toda a análise detalhada, com os gráficos gerados apartir dos dados, comparações de propriedades para investimento, e as conclusões chegadas ao final da análise.
https://github.com/brunocolombo/AirBnB_Orlando/blob/main/AirBnB_Orlando_Analysis.pdf


LinkedIn: [linkedin.com/in/bruno-colombo-/](https://www.linkedin.com/in/bruno-colombo-)
