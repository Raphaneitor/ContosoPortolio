# Sobre o Contoso
Contoso é uma empresa fictícia da Microsoft. Ela representa uma empresa multinacional de médio ou grande porte que opera em setores como: varejo, tecnologia, comércio eletrônico, fabricação e distribuição.

# Objetivo do Projeto
Este projeto analisa as vendas da empresa fictícia Contoso, utilizando o SQL Server para armazenamento e modelagem dos dados e Power BI para visualização. O objetivo é identificar tendências, oportunidades de crescimento e melhorar a eficiência operacional.
<br><br>
## Consulta dos Dados no SQL
O SQL foi escolhido porque oferece mais processamento, segurança e velocidade em comparação ao Excel. Isso garante que os dados estejam sempre íntegros, impedindo alterações indevidas e evitando problemas com arquivos corrompidos ou deslocados. 
O objetivo da consulta no banco de dados no SQL é trazer uma visão geral das vendas online por região, período e categoria dos produtos.<br>
<br>
<img align="middle" width="800"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/Select%20query_Contoso_FactOnlineSales.png?raw=true">
<br>
<br>
Primeiro realizamos uma consulta simples na tabela FactOnlineSales, para saber como os dados estão estruturados e quais informações podemos utilizar nas nossas futuras análises <br>
<br>
<img align="left" width="350" height="500" src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/Colunas_%20FactOnlineSales.png?raw=true">
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
Continuamos a nossa análise observando as colunas da Tabela FactOnlineSales, para que possamos também identificar quais outras tabelas estão vinculadas aos eventos dessa tabela fato, através das chaves estrangeiras presentes nela.<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br><br>


## Integração SQL Server - Power BI
É eficiente tanto em praticidade, segurança e facilidade analisar o banco de dados no SQL Server, mas para visualização de dados há somente tabelas. Com o Power BI, é possível demonstrar com mais opções de gráficos interativos os dados da empresa, moldados de acordo com a preferência do usuário final. O primeiro passo é a integração do SQL Server ao Power BI.
Passo a passo:
1.	Abrir o Power BI Desktop.
2.	Clicar em "Obter Dados" no menu superior.
3.	Selecionar "SQL Server" como fonte de dados.
4.	Preencher os detalhes da conexão, como servidor e o nome do banco de dados criado.
5.	Clicar em "Conectar".
<img align="middle" width="800"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/import%20de%20dados%20Contoso.png?raw=true">
Nota: caso queira utilizar o modo de conectividade de dados o de Importar, aumentará consideravelmente o tamanho do seu arquivo .pbix, pois ele irá baixar para o arquivo em questão todas as tabelas que forem selecionadas na hora da importação.
<br>
<br>
Já a opção de DirectQuery, ele fará um link direto com o banco de dados e não precisara baixar as tabelas, porem caso queira abrir esse arquivo de outro lugar, 
as tabelas não estarão disponíveis para visualização no powerBI, e sendo assim, veja qual a opção se encaixa melhor a sua situação.
<br><br>

## Relacionamento e modelagem dos dados
<img align="middle" width="800"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/Modelo%20Relacional%20de%20dados_Contoso.png?raw=true">
<b> Tabelas e colunas importadas, criadas e modeladas:</b> <br><br>
<b> - 1) FactOnlineSales:</b> Base para calcular métricas de desempenho, como total de vendas online, ticket médio e quantidade de produtos vendidos.<br><br>
<b>OnlineSalesKey:</b> Chave Primária para a tabela de FactOnlineSales. Representa o ID/número da venda.<br><br>
<b>DateKey:</b> Chave estrangeira para a tabela de dimensão de datas (DimCalendário). Representa a data em que a venda ocorreu.<br><br>
<b>StoreKey:</b> Chave estrangeira para a tabela de lojas (DimStore). Identifica a loja onde a venda ocorreu.<br><br>
<b>ProductKey:</b> Chave estrangeira para a tabela de dimensão de produtos (DimProduct). Indica qual produto foi vendido.<br><br>
<b>PromotionKey:</b> Chave estrangeira para a tabela de dimensão de descontos/promoções (DimPromotion). Indica se a venda teve alguma promoção/desconto.<br><br>
<b>CurrencyKey:</b> Chave estrangeira para a tabela de dimensão de moedas (DimCurrency). 
Indica qual tipo de moeda foi realizada na venda.<br><br>
<b>CustomerKey:</b> Chave estrangeira para a tabela de dimensão de clientes (DimCustomer). 
Indica qual cliente realizou a compra.<br><br>
<b>SalesOrderNumber:</b> Indica o número de Ordem da venda.<br><br>
<b>SalesOrderLineNumber:</b> Indica a linha do número de ordem da venda.<br><br>
<b>SalesQuantity:</b> Indica a quantidade vendida sobre aquele produto na venda.<br><br>
<b>SalesAmount:</b> Representa o total da venda<br><br>
<b>ReturnQuantity:</b> Indica uma possível quantidade de retorno na venda.<br><br>
<b>ReturnAmount: </b>Indica uma possível quantidade de retorno no valor da venda.<br><br>
<b>DiscountQuantity:</b> Indica a quantidade de descontos da venda.<br><br>
<b>DiscountAmount: </b>Indica o valor total de descontos na venda.<br><br>
<b>TotalCost: </b>Indica o Custo total da venda.<br><br>
<b>UnitCost:</b> Representa o custo unitário da venda<br><br>
<b>UnitPrice: </b>Indica o preço unitário da venda.<br><br>
<b>ETLLoadID: </b>ID de um possível processo de ETL da venda<br><br>
<b>LoadDate:</b> Data de um possível processo de carregamento dos dados da venda<br><br>
<b>UpdateDate: </b>Data de um possível processo de atualização dos dados da venda<br><br>
<br>
<b> - 2) DimProduct:</b> Permite análises por produto individual, como identificação dos itens mais vendidos ou com maior margem de lucro.<br><br>
<b>ProductKey:</b> Chave primária da tabela, usada para identificar cada produto de forma única. Também funciona como chave estrangeira na tabela FactSales.<br><br>
<b>ProductSubcategoryKey:</b> Chave estrangeira que referência a subcategoria do produto na tabela DimProductSubcategory.<br><br>
<b>AvailableForSaleDate:</b> Data em que o produto ficou disponível para venda.<br><br>
<b>StopSaleDate:</b> Data em que o produto foi descontinuado ou parou de ser vendido.<br><br>
<b>BrandName:</b> Nome da marca à qual o produto pertence.<br><br>
<b>ClassID:</b> Identificador numérico da classe do produto, usada para agrupar produtos similares.<br><br>
<b>ClassName:</b> Nome da classe do produto, como "Eletrodomésticos" ou "Eletrônicos".<br><br>
<b>StyleID:</b> número que identifica qual o tipo de estilo do produto<br><br>
<b>StyleName:</b> Nome do estilo do produto.<br><br>
<b>ColorID:</b> Número que representa qual a cor do produto.<br><br>
<b>ColorName:</b> Nome da cor do produto.<br><br>
<b>Size:</b> mostra qual o tamanho do produto.<br><br>
<b>SizeRange:</b> faixa de tamanho do produto.<br><br>
<b>SizeUnitMeasureID:</b> Possível ID que identifica a unidade de medida do produto.<br><br>
<b>Manufacturer:</b> Nome do fabricante do produto.<br><br>
<b>ProductDescription:</b> Descrição detalhada do produto.<br><br>
<b>ProductLabel:</b> Nome ou rótulo comercial do produto.<br><br>
<b>ProductName:</b> Nome do produto.<br><br>
<b>Status:</b> Status do produto (por exemplo, "Ativo" ou "Descontinuado").<br><br>
<b>UnitCost:</b> Custo unitário do produto (quanto a empresa paga para adquirir ou produzir).<br><br>
<b>UnitPrice:</b> Preço unitário do produto (quanto ele é vendido para os clientes).<br><br>
<b>Weight:</b> Peso do produto, útil para cálculos de frete e logística.<br><br>
<b>WeightUnitMeasureID:</b> Possível ID que identifica a unidade de peso do produto.<br><br>
<b>UnitOfMeasureName:</b> Nome da unidade de peso do produto.<br><br>
<b>StockTypeID:</b> Numero que representa o tipo de estoque onde o produto está guardado.<br><br>
<b>StockTypeName:</b> Nome do tipo de estoque onde o produto está guardado.<br><br>
<b>ImageURL:</b> link para a imagem do produto.<br><br>
<b>ProductURL:</b> link para a página do produto.<br><br>
<b>ETLLoadID:</b> ID de um possível processo de ETL do produto.<br><br>
<b>LoadDate:</b> Data de um possível processo de carregamento dos dados do produto.<br><br>
<b>UpdateDate:</b> Data de um possível processo de atualização dos dados do produto.<br><br>
<br>
<b> - 3) DimProductSubCategory: </b> Adiciona um nível intermediário de categorização entre o produto e a categoria principal, permitindo análises mais refinadas.<br><br>
<b>ProductSubcategoryKey:</b> Chave primária da tabela, usada para identificar cada subcategoria de produto de forma única. Também funciona como chave estrangeira na tabela (DimProduct).<br><br>
<b>ProductCategoryKey:</b> Chave estrangeira que referência a tabela DimProductCategory, indicando a qual categoria a subcategoria pertence.<br><br>
<b>ProductSubcategoryDescription:</b> Descrição detalhada da subcategoria do produto.<br><br>
<b>ProductSubcategoryLabel:</b> Nome ou rótulo comercial da subcategoria.<br><br>
<b>ProductSubcategoryName:</b> Nome da subcategoria do produto, como "Notebooks" ou "Smartphones".<br><br>
<b>ETLLoadID:</b> ID de um possível processo de ETL do produto.<br><br>
<b>LoadDate:</b> Data de um possível processo de carregamento dos dados do produto.<br><br>
<b>UpdateDate:</b> Data de um possível processo de atualização dos dados do produto.<br><br>
<br>
<b> - 4) DimProductCategory:</b> Permite agrupar os produtos em categorias amplas para análises estratégicas.<br><br>
<b>ProductCategoryKey:</b> Chave primária da tabela, usada para identificar cada categoria de produto de forma única. Também é referenciada na tabela DimProductSubCategory.<br><br>
<b>ProductCategoryDescription:</b> Descrição detalhada da categoria do produto.<br><br>
<b>ProductCategoryLabel:</b>  Nome ou rótulo comercial da categoria.<br><br>
<b>ProductCategoryName:</b> Nome da categoria do produto. <br><br>
<b>ETLLoadID:</b> ID de um possível processo de ETL do produto.<br><br>
<b>LoadDate:</b> Data de um possível processo de carregamento dos dados do produto.<br><br>
<b>UpdateDate:</b> Data de um possível processo de atualização dos dados do produto.<br><br>
<br>
<b> - 5) DimStore:</b> Permite avaliar o desempenho de pontos de venda individuais.<br><br>
<b>AdressLine1:</b> Primeira linha do endereço da loja (geralmente o nome da rua ou avenidas).<br><br>
<b>AdressLine2:</b>  Segunda linha do endereço da loja (geralmente usado para informações adicionais como número, complemento, etc.).<br><br>
<b>ZipCode:</b> Código postal (CEP) da loja.<br><br>
<b>ZipCodeExtension: </b>Extensão do código postal (geralmente utilizado para refinar a localização dentro de uma área maior).<br><br>
<b>GeographyKey:</b> Chave estrangeira para a tabela de geografia (DimGeography), representa uma localização específica ou região.<br><br>
<b>GeoLocation:</b> Localização geográfica da loja (geralmente um ponto de latitude e longitude).<br><br>
<b>Geometry:</b> Forma geométrica da loja ou de sua área de vendas, geralmente usada em cálculos espaciais, como determinar a proximidade de outras lojas.<br><br>
<b>OpenDate:</b> Data em que a loja foi inaugurada.<br><br>
<b>CloseDate:</b> Data em que a loja foi fechada.<br><br>
<b>Status:</b> Informa se a loja está atualmente ativa ou não.<br><br>
<b>CloseReason:</b> Motivo do fechamento da loja (por exemplo, "baixo desempenho", "reforma", etc.).<br><br>
<b>EmployeeCount:</b> Número de funcionários que trabalham na loja.<br><br>
<b>StoreManager:</b> Nome do gerente da loja.<br><br>
<b>StoreFax:</b> Número de fax da loja.<br><br>
<b>StorePhone:</b> Número de telefone da loja.<br><br>
<b>SellingAreaSize:</b> Tamanho da área de vendas da loja, geralmente medido em metros quadrados ou outra unidade de área.<br><br>
<b>LastRemodelDate:</b> Data da ultima remodelagem de dados da loja.<br><br>
<b>StoreType:</b> Tipo da loja (por exemplo, "loja física", "loja online", "revendedor", etc.).<br><br>
<b>StoreKey:</b> Chave primária da loja, usada para identificar a loja de forma única. Também é utilizada como chave estrangeira em tabelas fato, como FactSales.<br><br>
<b>EntityKey:</b> Identificador da entidade à qual a loja pertence.<br><br>
<b>StoreDescription:</b> Descrição detalhada da loja.<br><br>
<b>StoreName:</b> Nome da loja.<br><br>
<b>ETLLoadID:</b> ID de um possível processo de ETL da loja.<br><br>
<b>LoadDate:</b> Data de um possível processo de carregamento dos dados da loja.<br><br>
<b>UpdateDate:</b> Data de um possível processo de atualização dos dados da loja.<br><br>
<br>
<b> - 6) DimGeography: </b>Crucial para entender padrões de consumo por área.<br><br>
<b>GeographyKey: </b>Chave primária da tabela, usada para identificar cada localização de forma única. Também é referenciada por outras tabelas, como DimStore, para associar lojas a uma localização específica.<br><br>
<b>CityName: </b>Nome da cidade onde a loja está localizada.<br><br>
<b>StateProvinceName:</b> Nome do estado ou província ao qual a cidade pertence.<br><br>
<b>RegionCountryName:</b> Nome do país ou região a que pertence a cidade/estado.<br><br>
<b>ContinentName:</b> Nome do continente ao qual a localização pertence (por exemplo, "América do Norte" ou "Europa").<br><br>
<b>GeographyType:</b> Tipo da unidade geográfica representada (por exemplo, "Cidade", "Estado", "País").<br><br>
<b>Geometry:</b> Representação geométrica da localização, que pode incluir coordenadas espaciais (latitude/longitude) para análises geográficas avançadas.<br><br>
<b>ETLLoadID: </b>ID de um possível processo de ETL da região.<br><br>
<b>LoadDate:</b> Data de um possível processo de carregamento dos dados da região.<br><br>
<b>UpdateDate:</b> Data de um possível processo de atualização dos dados da região.<br><br>
<br>
<b> - 7) DimPromotion:</b> Permite agrupar quais produtos possuem algum tipo de promoção/desconto.<br><br>
<b>PromotionKey:</b> Chave primária da tabela, usada para identificar cada tipo de promoção de forma única. Também é referenciada na tabela FactOnlineSales.<br><br>
<b>PromotionLabel:</b> Outro número que serve para representar o ID/número do tipo de promoção do produto.<br><br>
<b>PromotionName:</b> Nome da promoção do produto.<br><br>
<b>PromotionDescription:</b> Descrição da promoção do produto.<br><br>
<b>DiscountPercent:</b> Porcentagem de desconto da promoção.<br><br>
<b>PromotionType:</b> Nome do tipo de promoção do produto.<br><br>
<b>PromotionCategory:</b> Nome da categoria da promoção.<br><br>
<b>StartDate:</b> Data de início da promoção.<br><br>
<b>EndDate: </b>Data de fim da promoção.<br><br>
<b>MinQty:</b>Quantidade mínima para o produto entrar na promoção na hora da venda.<br><br>
<b>MaxQty:</b> Quantidade máxima para o produto entrar na promoção na hora da venda.<br><br>
<b>ETLLoadID:</b> ID de um possível processo de ETL das promoções.<br><br>
<b>LoadDate:</b> Data de um possível processo de carregamento dos dados das promoções.<br><br>
<b>UpdateDate:</b> Data de um possível processo de atualização dos dados das promoções.<br><br>
<br>
<b> - 8) DimCustomer:</b> Permite agrupar as informações de todos os clientes das vendas.<br><br>
<b>CustomerKey:</b> Chave primária da tabela, usada para identificar o cliente de forma única. Também é referenciada na tabela FactOnlineSales.<br><br>
<b>GeographyKey:</b> Chave estrangeira para a tabela de dimensão de região (DimGeography). 
Indica de qual região o cliente realizou a compra.<br><br>
<b>CustomerLabel:</b> Outro número que serve para representar o ID/número do cliente.<br><br>
<b>Title:</b> Informa um possível título para o cliente.<br><br>
<b>FirstName:</b> Informa o primeiro nome do cliente.<br><br>
<b>MiddleName:</b> Informa o nome do meio do cliente.<br><br>
<b>LastName:</b> Informa o ultimo nome do cliente.<br><br>
<b>NameStyle:</b> Informa um possível estilo para o nome do cliente.<br><br>
<b>BirthDate:</b> informa a data de nascimento do cliente.<br><br>
<b>MaritalStatus:</b> Informa o estado civil do cliente.<br><br>
<b>Suffix:</b> Informa um possível sufixo no nome do cliente.<br><br>
<b>Gender:</b> Informa o gênero do cliente.<br><br>
<b>EmailAddress:</b> informa o e-mail do cliente.<br><br>
<b>YearlyIncome:</b> informa o quanto o cliente ganha em um ano.<br><br>
<b>TotalChildren:</b> informa o número total de filhos do cliente.<br><br>
<b>NumberChildrenAtHome:</b> Informa o número de filhos/crianças que o cliente possui em casa.<br><br>
<b>Education</b>: Informa o grau de formação do Cliente.<br><br>
<b>Occupation:</b> Informa o tipo de ocupação do Cliente.<br><br>
<b>HouseOwnerFlag:</b> Número que serve para identificar se o cliente é o proprietário da residência em que vive.<br><br>
<b>NumberCarsOwned:</b> número de carros que o cliente possui.<br><br>
<b>AddressLine1:</b> endereço informado pelo cliente.<br><br>
<b>AddressLine2:</b> possível segundo endereço informado pelo cliente.<br><br>
<b>Phone:</b> número de telefone do cliente.<br><br>
<b>DateFirstPurchase:</b> Data da primeira compra do cliente.<br><br>
<b>CustomerType:</b> Informa se o cliente é uma pessoa física ou jurídica.<br><br>
<b>CompanyName:</b> nome da empresa do cliente.<br><br>
<b>ETLLoadID: </b>ID de um possível processo de ETL dos clientes.<br><br>
<b>LoadDate:</b> Data de um possível processo de carregamento dos dados dos clientes.<br><br>
<b>UpdateDate:</b> Data de um possível processo de atualização dos dados dos clientes.<br><br>
<br>
<b> - 9) DimCurrency:</b> Agrupa quais tipos de moeda podem ser utilizadas nas vendas.<br><br>
<b>CurrencyKey:</b> Chave primária da tabela, usada para identificar qual tipo de moeda de forma única. Também é referenciada na tabela FactOnlineSales.<br><br>
<b>CurrencyLabel:</b> Outro número que serve para representar o ID/número do tipo de moeda.<br><br>
<b>CurrencyName:</b> Nome/Sigla da Moeda utilizada na hora da venda.<br><br>
<b>CurrencyDescription: </b>Informa a descrição com o nome da moeda<br><br>
<b>ETLLoadID: </b>ID de um possível processo de ETL das moedas.<br><br>
<b>LoadDate:</b> Data de um possível processo de carregamento dos dados das moedas.<br><br>
<b>UpdateDate:</b> Data de um possível processo de atualização dos dados das moedas.<br><br>
<br>
<b> - 10) DimCalendário:</b> Fundamental para análises temporais, como tendências de vendas ou sazonalidade.<br><br>
<b>Ano:</b> Representa o ano da data (exemplo: 2024).<br><br>
<b>Trimestre:</b> Número do trimestre do ano (1 para janeiro a março, 2 para abril a junho, etc.)<br><br>
<b>Quarter:</b> Geralmente uma versão em inglês do trimestre, usada para análises internacionais.<br><br>
<b>Date:</b> Representação completa da data no formato YYYY-MM-DD (exemplo: 2024-02-12).<br><br>
<b>Dia:</b> Número do dia do mês (exemplo: 12 para 12 de fevereiro).<br><br>
<b>Dia da Semana:</b> Número do dia na semana (1 para domingo, 2 para segunda-feira, etc.).<br><br>
<b>Nome do dia:</b> Nome do dia da semana (exemplo: "Segunda-feira").<br><br>
<b>Mês:</b> Número do mês dentro do ano (1 para janeiro, 2 para fevereiro, etc.).<br><br>
<b>Mês abrev: </b>Nome do mês abreviado (exemplo: "Jan", "Fev", "Mar").<br><br>
<b>Nome do Mês:</b> Nome completo do mês (exemplo: "Janeiro", "Fevereiro").<br><br>
<b>Semana do Ano:</b> Número da semana dentro do ano (1 para a primeira semana de janeiro, 2 para a segunda, etc.).<br><br>
<b>Semana do Mês: </b> Número da semana dentro do mês (1 para a primeira semana do mês, 2 para a segunda, etc.).<br><br>
<b>YearMonth: </b>Representação do ano e do mês no formato YYYYMM (exemplo: 202402 para fevereiro de 2024).<br><br>
<b>YearMonth desc: </b>Representação do ano e do mês no formato YYYYMM (exemplo: 202402 para fevereiro de 2024) em ordem decrescente.<br><br>

## Medidas

Seguindo com a nossa análise, agora criaremos uma nova tabela para organizar nossas medidas, indo em modelagem e depois em nova tabela. 
Vamos criar as medidas DAX para calcular o total de vendas, custos, margem de lucro, quantidade de vendas e vendas acumuladas no ano.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Vendas%20Amontoado.png?raw=true">

<b> - Vendas Amontoado:</b> Ajuda a identificar o desempenho das vendas em diferentes períodos, regiões ou categorias.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Vendas%20Amontoado%20LY.png?raw=true">

<b> - Vendas Amontoado LY (vendas do ano anterior):</b> Ajuda a identificar a magnitude das vendas em diferentes períodos, regiões ou categorias.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Vendas%20Amontoado%20LY%20Delta.png?raw=true">

<b> - Vendas Amontoado LY Delta (diferença de vendas):</b> Mostra o ganho ou perda de vendas em números.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Vendas%20Amontoado%20LY%20Delta%20%25.png?raw=true">

<b> - Vendas Amontoado LY Delta %: </b>Oferece uma perspectiva proporcional para entender a taxa de crescimento ou retração.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Vendas%20Delta%20%25%20txt.png?raw=true">

<b> - Vendas Delta % txt: </b>medida com formatação pré-estabelecida para mostrar em forma de texto a % da diferença de valores de venda entre um período com o outro.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Custo.png?raw=true">

<b> - Custo: </b>Permite monitorar o impacto das despesas operacionais nas finanças da empresa.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Custo%20LY.png?raw=true">

<b> - Custo LY (custo do ano anterior):</b> Permite identificar tendências de aumento ou redução de custos ao longo do tempo.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Custo%20LY%20Delta.png?raw=true">

<b> - Custo LY Delta: </b>Ajuda a identificar áreas específicas onde os custos cresceram ou foram otimizados.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Custo%20LY%20Delta%20%25.png?raw=true">

<b> - Custo LY Delta %: </b>Mostra a taxa de crescimento ou redução dos custos, proporcionalmente ao ano anterior.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Custo%20Delta%20%25%20txt.png?raw=true">

<b> - Custo Delta % txt: </b>medida com formatação pré-estabelecida para mostrar em forma de texto a % da diferença de valores de custo entre um período com o outro.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Margem%20Bruta.png?raw=true">

<b> - Margem Bruta: </b>Ajuda a identificar o valor de lucro gerado pela empresa em um período.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Margem%20Bruta%20LY.png?raw=true">

<b> - Margem BrutaLY:</b> Permite comparar a lucratividade atual com o desempenho histórico.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Margem%20Bruta%20Delta.png?raw=true">

<b> - Margem Bruta LY Delta: </b>Ajuda a identificar áreas específicas (regiões, produtos, categorias) onde a lucratividade foi impactada positivamente ou negativamente.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Margem%20Bruta%20Delta%20%25.png?raw=true">

<b> - Margem Bruta LY Delta %:</b> Ajuda a avaliar a eficácia das estratégias de controle de custos e aumento de vendas.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Margem%20Bruta%20Delta%20%25%20txt.png?raw=true">

<b> - Margem Bruta Delta % txt:</b> medida com formatação pré-estabelecida para mostrar em forma de texto a % da diferença de valores de margem bruta entre um período com o outro.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Vendas%20Quantidade.png?raw=true">

<b> - Vendas Quantidade:</b> Crucial para entender o volume de vendas e acompanhar o desempenho geral da empresa.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Vendas%20Quantidade%20LY.png?raw=true">

<b> - Vendas Quantidade LY (quantidade de vendas do ano passado):</b> Fundamental para avaliar o crescimento ou declínio nas quantidades de vendas.<br>  

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Vendas%20Quantidade%20LY%20Delta.png?raw=true">

<b> - Vendas Quantidade LY Delta:</b> Ajuda a identificar o impacto das mudanças no volume de vendas, revelando se as vendas estão aumentando ou diminuindo.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Vendas%20Quantidade%20LY%20Delta%20%25.png?raw=true">

<b> - Vendas Quantidade LY Delta %: </b>Ela é fundamental para apresentar o impacto das flutuações nas quantidades de vendas de maneira compreensível.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Vendas%20Quantidade%20Delta%20%25%20txt.png?raw=true">

<b> - Vendas Quantidade Delta % txt:</b> medida com formatação pré-estabelecida para mostrar em forma de texto a % da diferença de valores de quantidade de vendas entre um período com o outro.<br>

<img align="middle" width="500"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/medidas%20contoso/Desconto.png?raw=true">

<b> - Desconto:</b> Ajuda a identificar os valores de desconto nas vendas pela empresa em um período.<br>

<br><br>

## Principais métricas do dashboard e Conclusão do projeto
<img align="middle" width="800"  src="https://github.com/Raphaneitor/ContosoPortolio/blob/main/imagens/Contoso_Dashboard_Overview.png?raw=true">
<b> - Card de quantidade de vendas:</b> Mostra o volume total de unidades vendidas, útil para avaliar a demanda.<br><br>
<b> - Card de vendas:</b> Destaca o total de vendas, fornecendo um indicador rápido do desempenho geral.<br><br>
<b> - Card de custos:</b> Ajuda a monitorar os gastos, essencial para avaliar a eficiência operacional.<br><br>
<b> - Card de Margem de lucro:</b> Demonstra a rentabilidade da empresa, combinando vendas e custos.<br><br>
<b> - Tipos de Classe:</b> Mostra quais os principais tipos de classe de produtos vendem na Empresa. No caso do Contoso, na maior parte do tempo, mais de 60% das vendas são de classe regular,
fazendo que ela tenha uma dependência considerável sobre esse tipo de produto. Como sugestão, seria melhor criar mais descontos na parte de produtos econômicos e deluxe por exemplo, para tentar diversificar os lucros com um maior número de vendas.<br><br>
<b> - Vendas por continente:</b> Identifica os mercados mais rentáveis e permite análises geográficas estratégicas.<br><br>
<b> - Vendas por categoria de Produto:</b> Revela quais produtos ou categorias têm maior impacto nas vendas, apoiando decisões de portfólio. TOP 5 produtos mais vendidos representa 0,04% das vendas totais. 
Isso mostra que a Contoso tem um portfólio diversificado, sem grande dependência de poucos produtos, o que reduz riscos financeiros<br><br>
<b> - Venda por mês:</b> Permite identificar sazonalidades, tendências mensais e períodos de pico ou queda. Detectamos uma queda sazonal no início do ano e sugerimos promoções estratégicas, como “Volta às Aulas”, para minimizar o impacto.<br><br>
<b> - Custo/Vendas por mês:</b> Compara o custo de logística/fabricação dos produtos com o de vendas por mês ao longo do ano, ajudando a monitorar o progresso e planejar ações corretivas.<br><br>
<b> - Filtros dinâmicos:</b> Permitem personalizar as visualizações, tornando os dados relevantes para diferentes usuários e contextos.<br><br>
<b> - Tooltips (detalhamento):</b> Oferecem informações adicionais ao passar o cursor, enriquecendo as análises sem poluir o layout.<br><br>
<b> - Drill-through (tabela de detalhe das vendas):</b> Oferecem informações detalhadas ao selecionar qualquer medida com o botão direito e selecionar o Drill-through para o dashboard de vendas online detalhes, deixando as analises muito mais profundas.<br><br>

<br><br>
## Conclusão
Este projeto demonstra como a análise de dados pode transformar informações brutas em decisões estratégicas. Com insights claros sobre tendências de vendas, 
sazonalidade e lucratividade, as empresas podem ajustar suas estratégias para maximizar o crescimento e a eficiência operacional.

## Ferramentas e linguagens utilizadas
<div style="display: inline_block">
    <img align="center" alt="SQL" height="40" width="40" src="https://github.com/Raphaneitor/Portfolio/blob/main/linguagens/sql.png?raw=true">
    <img align="center" alt="Power BI" height="40" width="40" src="https://github.com/Raphaneitor/Portfolio/blob/main/linguagens/power%20bi.png?raw=true">
</div>
