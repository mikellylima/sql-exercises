## Módulo 4: Introdução ao SQL

### Aula 2: Criando uma Nova Consulta e usando SELECT FROM
- Selecionando todas as linhas e colunas da tabela DimCustomer
```sql
SELECT * FROM DimCustomer
```

- Selecionando todas as linhas e colunas da tabela DimStore
```sql
SELECT * FROM DimStore
```

- Selecionando todas as linhas da tabela DimCustomer, especificamente as colunas StoreKey, StoreName, StorePhone
```sql
SELECT StoreKey, StoreName, StorePhone FROM DimStore
```

- Selecionando todas as linhas e colunas da tabela DimProduct
```sql
SELECT * FROM DimProduct
```

- Selecionando todas as linhasda tabela DimProduct, especificamente as colunas ProductName, BrandName
```sql
SELECT ProductName, BrandName FROM DimProduct
```


### Aula 3: Salvando a primeira consulta e resolvendo 2 problemas
- Selecionando todas as linhas e colunas da tabela DimCustomer

```sql
SELECT * FROM DimCustomer
```

- Selecionando todas as linhas e colunas da tabela DimStore

```sql
SELECT * FROM DimStore
```

- Selecionando todas as linhas da tabela DimCustomer, especificamente as colunas StoreKey, StoreName, StorePhone

```sql
SELECT StoreKey, StoreName, StorePhone FROM DimStore
```

- Selecionando todas as linhas e colunas da tabela DimProduct

```sql
SELECT * FROM DimProduct
```

- Selecionando todas as linhas da tabela DimProduct, especificamente as colunas ProductName, BrandName

```sql
SELECT ProductName, BrandName FROM DimProduct
```


### Aula 4: Como organizar melhor os códigos com indentação
- Para organizar melhor os seus códigos, pule linhas. Abaixo temos dois exemplos de códigos que chegam no mesmo resultado, só que na versão 1, não utilizamos a indentação, e na versão 2, usamos. Observe que fica muito mais organizado.

- Selecionando todas as linhas e colunas da tabela DimStore
- versão 1

```sql
SELECT * FROM DimStore
```

- versão 2

```sql
SELECT 
	* 
FROM 
	DimStore
```

- Selecionando todas as linhas da tabela DimCustomer, especificamente as colunas StoreKey, StoreName, StorePhone
- versão 1

```sql
SELECT StoreKey, StoreName, StorePhone FROM DimStore
```

- versão 2

```sql
SELECT 
	StoreKey, 
	StoreName, 
	StorePhone 
FROM 
	DimStore
```


### Aula 5: Criando comentários em SQL
- Comentários em códigos têm 3 grandes finalidades:

- 1. Criar uma frase que explica o funcionamento de um determinado código
- Este código seleciona as colunas de ID do produto e nome do produto da tabela de produto

```sql
SELECT
	ProductKey,
	ProductName
FROM
	DimProduct
```

- 2. Comentar apenas parte de um código (para não apagar) e executar o restante

```sql
SELECT
	-- StoreKey,
	StoreName,
	StorePhone
FROM
	DimStore
```

- 3. Comentar todo o trecho de um código utilizando o /* ... */

```sql
/*
SELECT
	StoreKey,
	StoreName,
	StorePhone
FROM
	DimStore
*/
```

### Aula 6: SELECT TOP e TOP PERCENT
- Comando SELECT TOP(N) e TOP(N) PERCENT: Retorna as N primeiras linhas
- 1. Crie um código que retorna as 10 primeiras linhas da tabela de Produtos.

```sql
SELECT TOP(10) * FROM DimProduct
```


- 2. Retorna as 10% primeiras linhas da tabela de Clientes

```sql
SELECT TOP(10) PERCENT * FROM DimCustomer
```


### Aula 7: SELECT DISTINCT
- Comando SELECT DISTINCT: Retorna os valores distintos de 1 ou mais colunas de uma tabela
- Retorne todas as linhas da tabela DimProduct

```sql
SELECT * FROM DimProduct
```

- Retorne os valores distintos da coluna ColorName da tabela DimProduct

```sql
SELECT DISTINCT ColorName FROM DimProduct
```

- Retorne todas as linhas da tabela DimEmployee

```sql
SELECT * FROM DimEmployee
```

- Retorne os valores distintos da coluna DepartmentName da tabela DimEmployee

```sql
SELECT
	DISTINCT DepartmentName
FROM DimEmployee
```


### Aula 8: Renomeando colunas (aliasing)
- Comando AS: Renomeando colunas (aliasing)
- Selecione as 3 colunas da tabela DimProduct: ProductName, BrandName e ColorName

```sql
SELECT
	ProductName AS Produto,
	BrandName AS Marca,
	ColorName AS Cor
FROM 
	DimProduct
```


### Aula 11: Exercício 1 - Resolução
- Você é responsável por controlar os dados de clientes e de produtos da sua empresa. O que você precisará fazer é confirmar se:
- a. Existem 2.517 produtos cadastrados na base e, se não tiver, você deverá reportar ao seu gestor para saber se existe alguma defasagem no controle dos produtos.

```sql
SELECT DISTINCT ProductName FROM DimProduct
```

- b. Até o mês passado, a empresa tinha um total de 19.500 clientes na base de controle. Verifique se esse número aumentou ou reduziu.

```sql
SELECT * FROM DimCustomer
```

### Aula 12: Exercício 2 - Resolução
- Você trabalha no setor de marketing da empresa Contoso e acaba de ter uma ideia de oferecer descontos especiais para os clientes no dia de seus aniversários. Para isso, você vai precisar listar todos os clientes e as suas respectivas datas de nascimento, além de um contato.
- a) Selecione as colunas: CustomerKey, FirstName, EmailAddress, BirthDate da tabela dimCustomer.

```sql
SELECT 
	CustomerKey,
	FirstName,
	EmailAddress,
	BirthDate
FROM
	DimCustomer
```

- b) Renomeie as colunas dessa tabela usando o alias (comando AS).

```sql
SELECT 
	CustomerKey AS 'ID cliente',
	FirstName AS 'Primeiro nome',
	EmailAddress AS 'E-mail',
	BirthDate AS 'Data de nascimento'
FROM
	DimCustomer
```

### Aula 13: Exercício 3 - Resolução
- A Contoso está comemorando aniversário de inauguração de 10 anos e pretende fazer uma ação de premiação para os clientes. A empresa quer presentear os primeiros clientes desde a inauguração. Você foi alocado para levar adiante essa ação. Para isso, você terá que fazer o seguinte:
- a) A Contoso decidiu presentear os primeiros 100 clientes da história com um vale compras de R$ 10.000. Utilize um comando em SQL para retornar uma tabela com os primeiros 100 primeiros clientes da tabela dimCustomer (selecione todas as colunas).

```sql
SELECT TOP (100) * FROM DimCustomer
```

b) A Contoso decidiu presentear os primeiros 20% de clientes da história com um vale compras de R$ 2.000. Utilize um comando em SQL para retornar 10% das linhas da sua
tabela dimCustomer (selecione todas as colunas).

```sql
SELECT TOP (20) PERCENT * FROM DimCustomer
```

c) Adapte o código do item a) para retornar apenas as 100 primeiras linhas, mas apenas as colunas FirstName, EmailAddress, BirthDate.

```sql
SELECT TOP (20) PERCENT
	FirstName,
	EmailAddress,
	BirthDate
FROM DimCustomer
```

d) Renomeie as colunas anteriores para nomes em português.

```sql
SELECT TOP (20) PERCENT
	FirstName AS 'Primeiro nome',
	EmailAddress AS 'E-mail',
	BirthDate AS 'Data de nascimento'
FROM DimCustomer
```

### Aula 14: Exercício 4 - Resolução
- A empresa Contoso precisa fazer contato com os fornecedores de produtos para repor o estoque. Você é da área de compras e precisa descobrir quem são esses fornecedores. Utilize um comando em SQL para retornar apenas os nomes dos fornecedores na tabela dimProduct e renomeie essa nova coluna da tabela.

```sql
SELECT DISTINCT 
	Manufacturer AS 'Fornecedor'
FROM DimProduct
```

### Aula 15: Exercício 5 - Resolução
- O seu trabalho de investigação não para. Você precisa descobrir se existe algum produto registrado na base de produtos que ainda não tenha sido vendido. Tente chegar nessa informação.
Obs: caso tenha algum produto que ainda não tenha sido vendido, você não precisa descobrir qual é, é suficiente saber se teve ou não algum produto que ainda não foi vendido.

```sql
SELECT * FROM DimProduct
SELECT DISTINCT
	ProductKey
FROM FactSales
```


--------
##  Módulo 5: Ordenando e filtrando dados

### Aula 2: Order By (Parte 1)
- Selecionando as TOP 100 linhas da tabela DimStore, ordenando pela coluna EmployeeCount de forma decrescente

```sql
SELECT TOP(100) * FROM DimStore
ORDER BY EmployeeCount DESC
```


### Aula 3: Order By (Parte 2)
- Selecionando as TOP 10 linhas da tabela DimProduct, ordenando pelas colunas UnitCost (decrescente) e Weight (decrescente)

```sql
SELECT 
	TOP(10) ProductName,
	UnitCost,
	Weight
FROM
	DimProduct
ORDER BY UnitCost DESC, Weight DESC
```


### Aula 4: Where (Pt. 1) - Filtrando colunas de números
- Podemos filtrar os dados nas nossas tabelas utilizando o comando WHERE
- Quantos produtos têm um preço unitário maior que $1000?

```sql
SELECT 
	ProductName AS Produto,
	UnitPrice AS Preco
FROM
	DimProduct
WHERE UnitPrice >= 1000
```


### Aula 5: Where (Pt. 2) - Filtrando colunas de texto
- Podemos filtrar os dados nas nossas tabelas utilizando o comando WHERE
- Quais produtos são da marca 'Fabrikam'?

```sql
SELECT * FROM DimProduct
WHERE BrandName = 'Fabrikam'
```

- Quais produtos são da cor 'Black'?

```sql
SELECT * FROM DimProduct
WHERE ColorName = 'Black'
```


### Aula 6: Where (Pt. 3) - Filtrando colunas de data
- Podemos filtrar os dados nas nossas tabelas utilizando o comando WHERE
- Quais clientes nasceram após o dia 31/12/1970?

```sql
SELECT * FROM DimCustomer
WHERE BirthDate >= '1970-12-31'
ORDER BY BirthDate DESC
```


### Aula 8: Where mais And - Filtrando com mais de uma condição
- Podemos filtrar os dados nas nossas tabelas utilizando o comando WHERE
- Quais produtos são da marca 'Fabrikam' E TAMBÉM são da cor 'Black'?

```sql
SELECT * FROM DimProduct
WHERE BrandName = 'Fabrikam' AND ColorName = 'Black'
```


### Aula 9: Where mais Or - Filtrando com mais de uma condição
- Podemos filtrar os dados nas nossas tabelas utilizando o comando WHERE
- Quais produtos são da marca 'Contoso' OU são da cor 'White'?

```sql
SELECT * FROM DimProduct
WHERE BrandName = 'Contoso' OR ColorName = 'White'
```


### Aula 10: Where mais Not - Negando o filtro utilizado
- Podemos filtrar os dados nas nossas tabelas utilizando o comando WHERE
- Quais funcionários NÃO são do departamento de 'Marketing'?

```sql
SELECT * FROM DimEmployee
WHERE NOT DepartmentName = 'Marketing'
```


### Aula 11: Exercícios de Fixação - Where mais And, Or e Not
- Podemos filtrar os dados nas nossas tabelas utilizando o comando WHERE
- 1. Selecione todas as linhas da tabela DimEmployee de funcionários do sexo feminino E do departamento de finanças.

```sql
SELECT * FROM DimEmployee
WHERE Gender = 'F' AND DepartmentName = 'Finance'
```

- 2. Selecione todas as linhas da tabela DimProduct de produtos Contoso E da cor vermelha E que tenham um UnitPrice maior ou igual a $100.

```sql
SELECT * FROM DimProduct
WHERE BrandName = 'Contoso' AND ColorName = 'Red' AND UnitPrice >= 100
```

- 3. Selecione todas as linhas da tabela DimProduct com produtos da marca Litware OU da marca Fabrikam OU da cor Preta.

```sql
SELECT * FROM DimProduct
WHERE BrandName = 'Litware' OR BrandName = 'Fabrikam' OR ColorName = 'Black'
```

- 4. Selecione todas as linhas da tabela DimSalesTerritory onde o continente é a Europa mas o país NÃO é a Itália.

```sql
SELECT * FROM DimSalesTerritory
WHERE SalesTerritoryGroup = 'Europe' AND NOT SalesTerritoryCountry = 'Italy'
```


### Aula 12: Cuidados ao combinar os operadores AND e OR
- Podemos filtrar os dados nas nossas tabelas utilizando o comando WHERE
- Exemplo: Selecione todas as linhas da tabela DimProduct onde a cor do Produto pode ser igual a Preto OU Vermelho, MAS a marca deve ser obrigatoriamente igual a Fabrikam. Obs: Lembre-se de incluir parênteses para agrupar os testes lógicos que você deseja fazer ao mesmo tempo, para assim chegar no resultado que você espera.

```sql
SELECT * FROM DimProduct
WHERE (ColorName = 'Black' OR ColorName = 'Red') AND BrandName = 'Fabrikam'
```


### Aula 13: Where mais IN - Alternativa ao OR com múltiplas condições
- Podemos utilizar o operador IN como alternativa aos múltiplos OR.
- Exemplo: Selecione os funcionários que são de qualquer um desses 3 departamentos: Production, Marketing, Engineering.

```sql
SELECT * FROM DimEmployee
WHERE DepartmentName IN ('Production', 'Marketing', 'Engineering')
```


### Aula 14: Where mais Like - Filtro especial para textos
- 1. Selecione todos os produtos que possuem o texto 'MP3 Player' contido na nome do produto.

```sql
SELECT * FROM DimProduct
WHERE ProductName LIKE '%MP3 Player%'
```

- 2. Selecione todos os produtos que têm a descrição do nome começando por 'Type'.

```sql
SELECT * FROM DimProduct
WHERE ProductDescription LIKE 'Type%'
```

- 3. Selecione todos os produtos que têm a descrição do nome terminando em 'WMA'.

```sql
SELECT * FROM DimProduct
WHERE ProductDescription LIKE 'WMA%'
```


### Aula 15: Where mais Between - Filtrando entre valores
- 1. Selecione os funcionários que têm a data de contratação entre '01-01-2000' e '31-12-2000'.

```sql
SELECT * FROM DimEmployee
WHERE HireDate BETWEEN '2000-01-01' AND '2000-12-31'
```


### Aula 16: Where mais Is Null e Is Not Null - Filtrando valores nulos
- 1. Selecione os clientes que são pessoa física.

```sql
SELECT * FROM DimCustomer
WHERE CompanyName IS NULL
```


### Aula 18: Resolução Exercício 1
- Você é o gerente da área de compras e precisa criar um relatório com as TOP 100 vendas, de acordo com a quantidade vendida. Você precisa fazer isso em 10min pois o diretor de compras solicitou essa informação para apresentar em uma reunião. Utilize seu conhecimento em SQL para buscar essas TOP 100 vendas, de acordo com o total vendido (SalesAmount).

```sql
SELECT 
	TOP(100) * 
FROM 
	FactSales
ORDER BY 
	SalesQuantity DESC
```


### Aula 19: Resolução Exercício 2
- Os TOP 10 produtos com maior UnitPrice possuem exatamente o mesmo preço. Porém, a empresa quer diferenciar esses preços de acordo com o peso (Weight) de cada um.
O que você precisará fazer é ordenar esses top 10 produtos, de acordo com a coluna de UnitPrice e, além disso, estabelecer um critério de desempate, para que seja mostrado na ordem, do maior para o menor. Caso ainda assim haja um empate entre 2 ou mais produtos, pense em uma forma de criar um segundo critério de desempate (além do peso).

```sql
SELECT 
	TOP(10) *
FROM 
	DimProduct
ORDER BY UnitPrice DESC, Weight DESC, AvailableForSaleDate
```


### Aula 20: Resolução Exercício 3
- Você é responsável pelo setor de logística da empresa Contoso e precisa dimensionar o transporte de todos os produtos em categorias, de acordo com o peso. Os produtos da categoria A, com peso acima de 100kg, deverão ser transportados na primeira leva. Faça uma consulta no banco de dados para descobrir quais são estes produtos que estão na categoria A.

- a) Você deverá retornar apenas 2 colunas nessa consulta: Nome do Produto e Peso.

```sql
SELECT 
	ProductName, 
	Weight 
FROM 
	DimProduct
WHERE Weight > 100
```

- b) Renomeie essas colunas com nomes mais intuitivos.

```sql
SELECT 
	ProductName AS 'Nome do produto', 
	Weight AS 'Peso'
FROM 
	DimProduct
WHERE Weight > 100
```

- c) Ordene esses produtos do mais pesado para o mais leve.

```sql
SELECT 
	ProductName AS 'Nome do produto', 
	Weight AS 'Peso'
FROM 
	DimProduct
WHERE Weight > 100
ORDER BY Weight DESC
```


### Aula 21: Resolução Exercício 4
- Você foi alocado para criar um relatório das lojas registradas atualmente na Contoso.
- a) Descubra quantas lojas a empresa tem no total. Na consulta que você deverá fazer à tabela DimStore, retorne as seguintes informações: StoreName, OpenDate, EmployeeCount.

```sql
SELECT DISTINCT StoreName FROM DimStore
-- A Contoso tem 306 lojas
SELECT 
	StoreName, 
	OpenDate, 
	EmployeeCount
FROM 
	DimStore
```

- b) Renomeeie as colunas anteriores para deixar a sua consulta mais intuitiva.

```sql
SELECT 
	StoreName AS 'Nome da loja', 
	OpenDate AS 'Data de abertura', 
	EmployeeCount AS 'Numero de funcionarios'
FROM 
	DimStore
```

- c) Dessas lojas, descubra quantas (e quais) lojas ainda estão ativas.

```sql
SELECT 
	StoreName AS 'Nome da loja', 
	OpenDate AS 'Data de abertura', 
	EmployeeCount AS 'Numero de funcionarios',
	Status
FROM 
	DimStore
WHERE StoreType = 'Store' AND Status = 'On'
```


### Aula 22: Resolução Exercício 5
- O gerente da área de controle de qualidade notificou à Contoso que todos os produtos Home Theater da marca Litware, disponibilizados para venda no dia 15 de março de 2009, foram identificados com defeitos de fábrica. O que você deverá fazer é identificar os ID’s desses produtos e repassar ao gerente para que ele possa notificar as lojas e consequentemente solicitar a suspensão das vendas desses produtos.

```sql
SELECT 
	*
FROM 
	DimProduct
WHERE ProductName LIKE '%Home Theater%' AND BrandName = 'Litware' AND AvailableForSaleDate = '20090315'
```


### Aula 23: Resolução Exercício 6
- Imagine que você precise extrair um relatório da tabela DimStore, com informações de lojas. Mas você precisa apenas das lojas que não estão mais funcionando atualmente.
- a) Utilize a coluna de Status para filtrar a tabela e trazer apenas as lojas que não estão mais funcionando.

```sql
SELECT 
	* 
FROM 
	DimStore
WHERE Status = 'Off'
```

- b) Agora imagine que essa coluna de Status não existe na sua tabela. Qual seria a outra forma que você teria de descobrir quais são as lojas que não estão mais funcionando?

```sql
SELECT 
	* 
FROM 
	DimStore
WHERE CloseDate IS NOT NULL
```


### Aula 24: Resolução Exercício 7
- De acordo com a quantidade de funcionários, cada loja receberá uma determinada quantidade de máquinas de café. As lojas serão divididas em 3 categorias:
- Identifique, para cada caso, quais são as lojas de cada uma das 3 categorias acima (basta fazer uma verificação).
	- CATEGORIA 1: De 1 a 20 funcionários -> 1 máquina de café
	- CATEGORIA 2: De 21 a 50 funcionários -> 2 máquinas de café
	- CATEGORIA 3: Acima de 51 funcionários -> 3 máquinas de café

```sql
-- CATEGORIA 1
SELECT 
	* 
FROM 
	DimStore
WHERE EmployeeCount BETWEEN '1' AND '20'
-- 75 LOJAS

-- CATEGORIA 2
SELECT * FROM DimStore
WHERE EmployeeCount BETWEEN '21' AND '50'
-- 187 LOJAS

-- CATEGORIA 3
SELECT * FROM DimStore
WHERE EmployeeCount > 51
-- 43 LOJAS
```


### Aula 25: Resolução Exercício 8
- A empresa decidiu que todas as televisões de LCD receberão um super desconto no próximo mês. O seu trabalho é fazer uma consulta à tabela DimProduct e retornar os ID’s, Nomes e Preços de todos os produtos LCD existentes.

```sql
SELECT 
	ProductKey, 
	ProductName, 
	UnitPrice 
FROM 
	DimProduct
WHERE ProductDescription LIKE '%LCD%'
```


### Aula 26: Resolução Exercício 9
- Faça uma lista com todos os produtos das cores: Green, Orange, Black, Silver e Pink. Estes produtos devem ser exclusivamente das marcas: Contoso, Litware e Fabrikam.

```sql
SELECT 
	* 
FROM 
	DimProduct
WHERE ColorName IN ('Green', 'Orange', 'Black', 'Silver', 'Pink') AND BrandName IN ('Contoso', 'Litware', 'Fabrikam')
```


### Aula 27: Resolução Exercício 10
- A empresa possui 16 produtos da marca Contoso, da cor Silver e com um UnitPrice entre 10 e 30. Descubra quais são esses produtos e ordene o resultado em ordem decrescente de acordo com o preço (UnitPrice).

```sql
SELECT 
	ProductName, 
	BrandName, 
	ColorName, 
	UnitPrice
FROM 
	DimProduct
WHERE BrandName = 'Contoso' AND ColorName = 'Silver' AND UnitPrice BETWEEN '10' AND '30'
ORDER BY UnitPrice DESC
```

-----------
##  Módulo 6: Funções de Agregação

### Aula 2: Função SUM
- 1. Faça uma consulta que retorna a soma total de SalesQuantity e a soma total de ReturnQuantity.

```sql
SELECT
	SUM(SalesQuantity) AS 'Total Vendido',
	SUM(ReturnQuantity) AS 'Total Devolvido'
FROM
	FactSales
```


### Aula 3: Função COUNT
- 1. Faça uma consulta que retorna a contagem total de produtos. Considere a coluna ProductName para este cálculo. Obs: A função COUNT não conta valores nulos da coluna, então tome cuidado com o resultado que você espera.

```sql
SELECT
	COUNT(ProductName) AS 'Qtd. Produtos'
FROM
	DimProduct
```

- 2. Faça uma consulta que retorna a contagem total de produtos. Considere a coluna Size para este cálculo

```sql
SELECT
	COUNT(Size) AS 'Qtd. Produtos'
FROM
	DimProduct
```


### Aula 4: Função COUNT mais DISTINCT
- 1. Faça uma consulta que retorna a contagem distinta das marcas dos produtos

```sql
SELECT
	COUNT(DISTINCT BrandName)
FROM
	DimProduct
```


### Aula 5: Funções MIN e MAX
- 1. Faça uma consulta que retorna os valores máximo e mínimo de UnitCost.

```sql
SELECT
	MAX(UnitCost) AS 'Custo Máximo',
	MIN(UnitCost) AS 'Custo Mínimo'
FROM
	DimProduct
```


### Aula 6: Função AVG
- 1. Faça uma consulta que retorna a média de YearlyIncome (média de salário) da tabela DimCustomer.

```sql
SELECT
	AVG(YearlyIncome) AS 'Média Anual de Salário'
FROM
	DimCustomer
```


### Aula 8: Resolução Exercício 1
- O gerente comercial pediu a você uma análise da Quantidade Vendida e Quantidade Devolvida para o canal de venda mais importante da empresa: Store. Utilize uma função SQL para fazer essas consultas no seu banco de dados. Obs: Faça essa análise considerando a tabela FactSales.

```sql
SELECT TOP(10) * FROM FactSales
SELECT * FROM DimChannel

SELECT 
	SUM(SalesQuantity) AS 'Qtd. vendida',
	SUM(ReturnQuantity) AS 'Qtd. devolvida'
FROM
	FactSales
WHERE channelKey = '1'
-- Resp: qtd. vendida = 29089448; qtd. devolvida = 274205
```


### Aula 9: Resolução Exercício 2
- Uma nova ação no setor de Marketing precisará avaliar a média salarial de todos os clientes da empresa, mas apenas de ocupação Professional. Utilize um comando SQL para atingir esse resultado.

```sql
SELECT * FROM DimCustomer

SELECT
	AVG(YearlyIncome) AS 'Média salarial'
FROM
	DimCustomer
WHERE Occupation = 'Professional'
-- Resp: Média salarial de R$ 74184,7826
```


### Aula 10: Resolução Exercício 3
- Você precisará fazer uma análise da quantidade de funcionários das lojas registradas na empresa. O seu gerente te pediu os seguintes números e informações:
- a) Quantos funcionários tem a loja com mais funcionários?

```sql
SELECT
	MAX(EmployeeCount)
FROM
	DimStore
-- Resp: 325 funcionários
```

- b) Qual é o nome dessa loja?

```sql
SELECT
	StoreName
FROM
	DimStore
WHERE EmployeeCount = '325'

-- outra forma
SELECT
	TOP(1)
	StoreName AS 'Nome da Loja',
	EmployeeCount AS 'Qtd. de funcionarios'
FROM
	DimStore
ORDER BY EmployeeCount DESC
```

- c) Quantos funcionários tem a loja com menos funcionários?

```sql
SELECT
	MIN(EmployeeCount)
FROM
	DimStore
-- Resp: 7 funcionários
```

- d) Qual é o nome dessa loja?

```sql
SELECT
	StoreName
FROM
	DimStore
WHERE EmployeeCount = '7'

-- outra forma
SELECT
	TOP(1)
	StoreName AS 'Nome da Loja',
	EmployeeCount AS 'Qtd. de funcionarios'
FROM
	DimStore
WHERE EmployeeCount IS NOT NULL
ORDER BY EmployeeCount
-- Resp: Contoso Europe Online Store
```


### Aula 11: Resolução Exercício 4
- A área de RH está com uma nova ação para a empresa, e para isso precisa saber a quantidade total de funcionários do sexo Masculino e do sexo Feminino.
- a) Descubra essas duas informações utilizando o SQL.

```sql
SELECT
	COUNT(Gender) AS 'Feminino'
FROM
	DimEmployee
WHERE Gender =	'F'
-- Resp: 87 funcionaris do sexo F

SELECT
	COUNT(Gender) AS 'Masculino'
FROM
	DimEmployee
WHERE Gender =	'M'
-- Resp: 206 funcionaris do sexo F
```

b) O funcionário e a funcionária mais antigos receberão uma homenagem. Descubra as seguintes informações de cada um deles: Nome, E-mail, Data de Contratação.

```sql
SELECT
	TOP(1)
	FirstName AS 'Nome', 
	EmailAddress AS 'E-mail', 
	HireDate AS 'Data de Contratação'
FROM
	DimEmployee
WHERE Gender = 'F' 
ORDER BY HireDate
-- Resp: Terry, jolynn@contoso.com, HireDate = 1998-01-26

SELECT
	TOP(1)
	FirstName AS 'Nome', 
	EmailAddress AS 'E-mail', 
	HireDate AS 'Data de Contratação'
FROM
	DimEmployee
WHERE Gender = 'M' 
ORDER BY HireDate
-- Resp: Kim, guy1@contoso.com, HireDate = 1996-07-31
```

### Aula 12: Resolução Exercício 5
- Agora você precisa fazer uma análise dos produtos. Será necessário descobrir as seguintes informações:
- a) Quantidade distinta de cores de produtos.

```sql
SELECT
	COUNT(DISTINCT ColorName)
FROM
	DimProduct
-- Resp: 16 cores
```

- b) Quantidade distinta de marcas

```sql
SELECT
	COUNT(DISTINCT BrandName)
FROM
	DimProduct
-- Resp: 11 marcas
```

- c) Quantidade distinta de classes de produto

```sql
SELECT
	COUNT(DISTINCT ClassName)
FROM
	DimProduct
-- Resp: 3 classes
```


-------------
## Módulo 7: Criando agrupamentos no SQL

### Aula 2: Group By (Parte 1)

```sql
SELECT * FROM DimProduct

SELECT
	BrandName AS 'Nome da Marca',
	COUNT(*) AS 'Qtd Total'
FROM
	DimProduct
GROUP BY BrandName
```


### Aula 3: Group By (Parte 2)

```sql
-- Consulta 1
SELECT * FROM DimStore

SELECT
	StoreType,
	SUM(EmployeeCount) AS 'Qtd. Total Funcionários'
FROM
	DimStore
GROUP BY StoreType

-- Consulta 2
SELECT * FROM DimProduct

SELECT
	BrandName,
	AVG(UnitCost) AS 'Custo Médio'
FROM
	DimProduct
GROUP BY BrandName


-- Consulta 3
SELECT * FROM DimProduct

SELECT
	ClassName AS 'Classe do Produto',
	MAX(UnitPrice) AS 'Máximo Preço'
FROM
	DimProduct
GROUP BY ClassName
```


### Aula 4 de 18: Group By + Order By

```sql
SELECT
	StoreType,
	SUM(EmployeeCount) AS 'Qtd. Total Funcionários'
FROM
	DimStore
GROUP BY StoreType
ORDER BY SUM(EmployeeCount) DESC
```


### Aula 5: Group By + Where

```sql
SELECT * FROM DimProduct

SELECT
	ColorName AS 'Cor do Produto',
	COUNT(ColorName) AS 'Qtd. Total'
FROM
	DimProduct
WHERE BrandName = 'Contoso'
GROUP BY ColorName
```


### Aula 6: Group By + Having

```sql
SELECT
	BrandName AS 'Marca',
	COUNT(BrandName) AS 'Total Marca'
FROM
	DimProduct
GROUP BY BrandName

HAVING COUNT(BrandName) >= 200
```


### Aula 7: Where vs Having

```sql
SELECT
	BrandName AS 'Marca',
	COUNT(BrandName) AS 'Total Marca'
FROM
	DimProduct
WHERE ClassName = 'Economy'     -- Filtra a tabela original, antes do agrupamento
GROUP BY BrandName
HAVING COUNT(BrandName) >= 200  -- Filtra a tabela depois de agrupada
```


### Aula 9: Resolução Exercício 1
- a) Faça um resumo da quantidade vendida (SalesQuantity) de acordo com o canal de vendas (channelkey).

```sql
SELECT
	channelKey AS 'Canal',
	SUM(SalesQuantity) AS 'Qtd. vendida'
FROM
	FactSales
GROUP BY channelKey
```

- b) Faça um agrupamento mostrando a quantidade total vendida (SalesQuantity) e quantidade
total devolvida (Return Quantity) de acordo com o ID das lojas (StoreKey).

```sql
SELECT
	StoreKey AS 'ID loja',
	SUM(SalesQuantity) AS 'Qtd. vendida',
	SUM(ReturnQuantity) AS 'Qtd. devolvida'
FROM
	FactSales
GROUP BY StoreKey
```

- c) Faça um resumo do valor total vendido (SalesAmount) para cada canal de venda, mas apenas
para o ano de 2007.

```sql
SELECT
	channelKey AS 'Canal',
	SUM(SalesAmount) AS 'Qtd. vendida'
FROM
	FactSales
WHERE DateKey BETWEEN '20070101' AND '20071231'
GROUP BY channelKey
```


### Aula 10: Resolução Exercício 2
- Você precisa fazer uma análise de vendas por produtos. O objetivo final é descobrir o valor total vendido (SalesAmount) por produto (ProductKey).
- a) A tabela final deverá estar ordenada de acordo com a quantidade vendida e, além disso, mostrar apenas os produtos que tiveram um resultado final de vendas maior do que $5.000.000.

```sql
SELECT
	ProductKey AS 'Chave do produto',
	SUM(SalesAmount) AS 'Qtd. vendida'
FROM
	FactSales
GROUP BY ProductKey
HAVING SUM(SalesAmount) > 5000000
ORDER BY SUM(SalesAmount) DESC
```

- b) Faça uma adaptação no exercício anterior e mostre os Top 10 produtos com mais vendas. Desconsidere o filtro de $5.000.000 aplicado.

```sql
SELECT
	TOP(10)
	ProductKey AS 'Chave do produto',
	SUM(SalesAmount) AS 'Qtd. vendida'
FROM
	FactSales
GROUP BY ProductKey
ORDER BY SUM(SalesAmount) DESC
```


### Aula 11: Resolução Exercício 3
- a) Você deve fazer uma consulta à tabela FactOnlineSales e descobrir qual é o ID (CustomerKey) do cliente que mais realizou compras online (de acordo com a coluna
SalesQuantity).

```sql
SELECT TOP(10) * FROM FactOnlineSales

SELECT TOP(1) 
	CustomerKey AS 'ID cliente',
	SUM(SalesQuantity) AS 'Qtd. comprada'
FROM 
	FactOnlineSales
GROUP BY CustomerKey
ORDER BY SUM(SalesQuantity) DESC
```

- b) Feito isso, faça um agrupamento de total vendido (SalesQuantity) por ID do produto e descubra quais foram os top 3 produtos mais comprados pelo cliente da letra a).

```sql
SELECT TOP(3)
	ProductKey AS 'ID produto',
	SUM(SalesQuantity) AS 'Qtd. comprada'
FROM 
	FactOnlineSales
WHERE CustomerKey = 19037
GROUP BY ProductKey
ORDER BY SUM(SalesQuantity) DESC
```


### Aula 12: Resolução Exercício 4
- a) Faça um agrupamento e descubra a quantidade total de produtos por marca.

```sql
SELECT * FROM DimProduct

SELECT 
	BrandName AS 'Marca',
	COUNT(ProductName) AS 'Qtd. produtos'
FROM 
	DimProduct
GROUP BY BrandName
ORDER BY COUNT(ProductName) DESC
```

- b) Determine a média do preço unitário (UnitPrice) para cada ClassName.

```sql
SELECT 
	ClassName AS 'Classe',
	AVG(UnitPrice) AS 'Media Preço Unit.'
FROM 
	DimProduct
GROUP BY ClassName
ORDER BY AVG(UnitPrice) DESC
```

- c) Faça um agrupamento de cores e descubra o peso total que cada cor de produto possui.

```sql
SELECT 
	ColorName AS 'Cor',
	SUM(Weight) AS 'Peso da cor'
FROM 
	DimProduct
GROUP BY ColorName
ORDER BY SUM(Weight) DESC
```


### Aula 13: Resolução Exercício 5
- Você deverá descobrir o peso total para cada tipo de produto (StockTypeName). A tabela final deve considerar apenas a marca ‘Contoso’ e ter os seus valores classificados em ordem decrescente.

```sql
SELECT * FROM DimProduct

SELECT 
	StockTypeName AS 'Tipo de produto',
	SUM(Weight) AS 'Peso do produto',
	COUNT(BrandName) AS 'Marca Contoso'
FROM 
	DimProduct
WHERE BrandName = 'Contoso'
GROUP BY StockTypeName
ORDER BY SUM(Weight) DESC
```


### Aula 14: Resolução Exercício 6
- Você seria capaz de confirmar se todas as marcas dos produtos possuem à disposição todas as 16 opções de cores?

```sql
SELECT * FROM DimProduct

SELECT 
	BrandName AS 'Marca',
	COUNT(DISTINCT ColorName) AS 'Cores distintas'
FROM 
	DimProduct
GROUP BY BrandName
ORDER BY COUNT(DISTINCT ColorName)
```


### Aula 15: Resolução Exercício 7
- Faça um agrupamento para saber o total de clientes de acordo com o Sexo e também a média salarial de acordo com o Sexo. Corrija qualquer resultado “inesperado” com os seus conhecimentos em SQL.

```sql
SELECT * FROM DimCustomer

SELECT 
	Gender AS 'Gênero',
	COUNT(FirstName) AS	'Qtd. clientes',
	AVG(YearlyIncome) AS 'Média salarial'
FROM
	DimCustomer
WHERE Gender IS NOT NULL
GROUP BY Gender
```


### Aula 16: Resolução Exercício 8
- Faça um agrupamento para descobrir a quantidade total de clientes e a média salarial de acordo com o seu nível escolar. Utilize a coluna Education da tabela DimCustomer para fazer esse agrupamento.

```sql
SELECT 
	Education AS 'Escolaridade',
	COUNT(FirstName) AS	'Qtd. clientes',
	AVG(YearlyIncome) AS 'Média salarial'
FROM
	DimCustomer
WHERE Education IS NOT NULL
GROUP BY Education
ORDER BY AVG(YearlyIncome)
```


### Aula 17: Resolução Exercício 9
- Faça uma tabela resumo mostrando a quantidade total de funcionários de acordo com o Departamento (DepartmentName). Importante: Você deverá considerar apenas os funcionários ativos.

```sql
SELECT * FROM DimEmployee

SELECT 
	DepartmentName AS 'Departamento',
	COUNT(FirstName) AS 'Qtd. funcionarios'
FROM 
	DimEmployee
WHERE Status = 'Current'
GROUP BY DepartmentName
ORDER BY COUNT(FirstName) DESC

```


### Aula 18: Resolução Exercício 10
- Faça uma tabela resumo mostrando o total de VacationHours para cada cargo (Title). Você deve considerar apenas as mulheres, dos departamentos de Production, Marketing, Engineering e Finance, para os funcionários contratados entre os anos de 1999 e 2000.

```sql
SELECT * FROM DimEmployee

SELECT 
	Title AS 'Cargo',
	SUM(VacationHours) AS 'Horas totais'
FROM 
	DimEmployee
WHERE Gender = 'F' AND DepartmentName IN ('Production','Marketing','Engineering','Finance') AND HireDate BETWEEN '1999-01-01' AND '2000-12-31'
GROUP BY Title
ORDER BY SUM(VacationHours) DESC
```


-------------
## Módulo 8

### Aula 2: Por que precisamos do JOIN?

```sql
SELECT TOP(1000) * FROM FactSales
SELECT * FROM DimChannel

SELECT
	channelKey,
	SUM(SalesQuantity) AS 'Qtd. Vendida'
FROM
	FactSales
GROUP BY channelKey



SELECT TOP(1000) * FROM FactSales
SELECT * FROM DimProduct


SELECT TOP(1000) * FROM FactOnlineSales
SELECT * FROM DimCustomer


SELECT * FROM FactStrategyPlan
SELECT * FROM DimScenario
```


### Aula 3: Por que não criamos logo uma tabela com todas as informações pra facilitar?

```sql
SELECT TOP(1000) * FROM FactSales
SELECT * FROM DimProduct
```


### Aula 7: LEFT (OUTER) JOIN

```sql
SELECT * FROM produtos
SELECT * FROM subcategoria

SELECT
	produtos.id_produto,
	produtos.nome_produto,
	produtos.id_subcategoria,
	subcategoria.nome_subcategoria
FROM produtos
LEFT JOIN subcategoria
	ON produtos.id_subcategoria = subcategoria.id_subcategoria
```


### Aula 8: RIGHT (OUTER) JOIN

```sql
SELECT * FROM produtos
SELECT * FROM subcategoria

SELECT
	produtos.id_produto,
	produtos.nome_produto,
	produtos.id_subcategoria,
	subcategoria.nome_subcategoria
FROM produtos
RIGHT JOIN subcategoria
	ON produtos.id_subcategoria = subcategoria.id_subcategoria

```


### Aula 9: INNER JOIN

```sql
SELECT * FROM produtos
SELECT * FROM subcategoria

SELECT
	produtos.id_produto,
	produtos.nome_produto,
	produtos.id_subcategoria,
	subcategoria.nome_subcategoria
FROM produtos
INNER JOIN subcategoria
	ON produtos.id_subcategoria = subcategoria.id_subcategoria
```


### Aula 10: FULL (OUTER) JOIN

```sql
SELECT * FROM produtos
SELECT * FROM subcategoria

-- Considerando a coluna id_subcategoria da tabela produtos
SELECT
	produtos.id_produto,
	produtos.nome_produto,
	produtos.id_subcategoria,
	subcategoria.nome_subcategoria
FROM produtos
FULL JOIN subcategoria
	ON produtos.id_subcategoria = subcategoria.id_subcategoria


-- Considerando a coluna id_subcategoria da tabela subcategoria
SELECT
	produtos.id_produto,
	produtos.nome_produto,
	subcategoria.id_subcategoria,
	subcategoria.nome_subcategoria
FROM produtos
FULL JOIN subcategoria
	ON produtos.id_subcategoria = subcategoria.id_subcategoria
```


### Aula 11: LEFT, RIGHT e FULL ANTI JOIN

```sql
SELECT * FROM produtos
SELECT * FROM subcategoria


-- LEFT (ANTI) JOIN

SELECT
	produtos.id_produto,
	produtos.nome_produto,
	produtos.id_subcategoria,
	subcategoria.nome_subcategoria
FROM produtos
LEFT JOIN subcategoria
	ON produtos.id_subcategoria = subcategoria.id_subcategoria
WHERE nome_subcategoria IS NULL


-- RIGHT (ANTI) JOIN

SELECT
	produtos.id_produto,
	produtos.nome_produto,
	produtos.id_subcategoria,
	subcategoria.nome_subcategoria
FROM produtos
RIGHT JOIN subcategoria
	ON produtos.id_subcategoria = subcategoria.id_subcategoria
WHERE id_produto IS NULL


-- FULL (ANTI) JOIN

SELECT
	produtos.id_produto,
	produtos.nome_produto,
	produtos.id_subcategoria,
	subcategoria.nome_subcategoria
FROM produtos
FULL JOIN subcategoria
	ON produtos.id_subcategoria = subcategoria.id_subcategoria
WHERE id_produto IS NULL OR nome_subcategoria IS NULL
```


### Aula 12: INNER, LEFT e RIGHT JOIN - Exemplos

```sql
SELECT ProductKey, ProductName, ProductSubcategoryKey FROM DimProduct
SELECT ProductSubcategoryKey, ProductSubcategoryName FROM DimProductSubcategory

SELECT
	ProductKey,
	ProductName,
	DimProduct.ProductSubcategoryKey,
	ProductSubcategoryName
FROM DimProduct
INNER JOIN DimProductSubcategory
	ON DimProduct.ProductSubcategoryKey = DimProductSubcategory.ProductSubcategoryKey


SELECT
	ProductKey,
	ProductName,
	DimProduct.ProductSubcategoryKey,
	ProductSubcategoryName
FROM DimProduct
LEFT JOIN DimProductSubcategory
	ON DimProduct.ProductSubcategoryKey = DimProductSubcategory.ProductSubcategoryKey


SELECT
	ProductKey,
	ProductName,
	DimProduct.ProductSubcategoryKey,
	ProductSubcategoryName
FROM DimProduct
RIGHT JOIN DimProductSubcategory
	ON DimProduct.ProductSubcategoryKey = DimProductSubcategory.ProductSubcategoryKey

```


### Aula 13: Como definir quem é a LEFT Table e a RIGHT Table

```sql
-- 1. LEFT Join para complementar informações da tabela produtos (LEFT) de acordo com a tabela de categoria (RIGHT)
SELECT
	id_produto,
	nome_produto,
	produtos.id_subcategoria,
	nome_subcategoria
FROM produtos
LEFT JOIN subcategoria
	ON produtos.id_subcategoria = subcategoria.id_subcategoria


-- 2. Obtendo o LEFT Join do caso 1 usando um RIGHT Join e invertendo as tabelas de lado
SELECT
	id_produto,
	nome_produto,
	produtos.id_subcategoria,
	nome_subcategoria
FROM subcategoria
RIGHT JOIN produtos
	ON subcategoria.id_subcategoria = produtos.id_subcategoria

```


### Aula 15: CROSS JOIN

```sql
-- CROSS JOIN

-- PARA ACOMPANHAR ESTA AULA, PRECISAREMOS CRIAR A TABELA MARCAS

-- PRIMEIRO, GARANTA QUE NÃO EXISTE NENHUMA TABELA CHAMADA MARCAS NO BANCO DE DADOS, EXECUTANDO O COMANDO DROP TABLE ABAIXO:
DROP TABLE IF EXISTS marcas

-- AGORA CRIE A TABELA MARCAS:
CREATE TABLE marcas(
id_marca int,
marca varchar(30))


-- INSIRA AS LINHAS DA TABELA MARCAS:
INSERT INTO marcas(id_marca, marca)
VALUES
	(1, 'Apple'),
	(2, 'Samsung'),
	(3, 'Motorola')


SELECT * FROM marcas
SELECT * FROM subcategoria


SELECT
	marca,
	nome_subcategoria
FROM marcas CROSS JOIN subcategoria
```


### Aula 16: Múltiplos Joins

```sql
SELECT ProductKey, ProductName, ProductSubcategoryKey FROM DimProduct
SELECT ProductSubcategoryKey, ProductSubcategoryName, ProductCategoryKey FROM DimProductSubcategory
SELECT ProductCategoryKey, ProductCategoryName FROM DimProductCategory

SELECT
	ProductKey,
	ProductName,
	DimProduct.ProductSubcategoryKey,
	ProductCategoryName
FROM DimProduct
INNER JOIN DimProductSubcategory
	ON DimProduct.ProductSubcategoryKey = DimProductSubcategory.ProductSubcategoryKey
		INNER JOIN DimProductCategory
			ON DimProductSubcategory.ProductCategoryKey = DimProductCategory.ProductCategoryKey

```


### Aula 17: UNION e UNION ALL

```sql
-- UNION

SELECT
	*
FROM
	DimCustomer
WHERE Gender = 'F'
UNION
SELECT
	*
FROM
	DimCustomer
WHERE Gender = 'M'


-- UNION ALL

SELECT
	FirstName,
	BirthDate
FROM
	DimCustomer
WHERE Gender = 'F'
UNION ALL
SELECT
	FirstName,
	BirthDate
FROM
	DimCustomer
WHERE Gender = 'M'
```


### Aula 19: Resolução Exercício 1
- Utilize o INNER JOIN para trazer os nomes das subcategorias dos produtos, da tabela DimProductSubcategory para a tabela DimProduct.

```sql
SELECT TOP (10) * FROM DimProduct
SELECT TOP (10) * FROM DimProductSubcategory

SELECT
	ProductKey,
	ProductName,
	DimProduct.ProductSubcategoryKey,
	ProductSubcategoryName
FROM 
	DimProduct
INNER JOIN DimProductSubcategory
	ON DimProduct.ProductSubcategoryKey = DimProductSubcategory.ProductSubcategoryKey
-- INNER: 2517 linhas
-- LEFT: 2517 linhas
-- Todos os produtos estão classificados com uma subcategoria
```


### Aula 20: Resolução Exercício 2
- Identifique uma coluna em comum entre as tabelas DimProductSubcategory e DimProductCategory. Utilize essa coluna para complementar informações na tabela DimProductSubcategory a partir da DimProductCategory. Utilize o LEFT JOIN.

```sql
SELECT TOP (10) * FROM DimProductSubcategory
SELECT TOP (10) * FROM DimProductCategory
SELECT COUNT(*) FROM DimProductSubcategory
SELECT COUNT(*) FROM DimProductCategory

SELECT
	ProductSubcategoryKey,
	ProductSubcategoryName,
	DimProductSubcategory.ProductCategoryKey,
	ProductCategoryName
FROM 
	DimProductSubcategory
LEFT JOIN DimProductCategory
	ON DimProductSubcategory.ProductCategoryKey = DimProductCategory.ProductCategoryKey
-- INNER: 44 linhas.
-- LEFT: 44 linhas.
-- Todas as subcategorias tem uma categoria.
```


### Aula 21: Resolução Exercício 3
- Para cada loja da tabela DimStore, descubra qual o Continente e o Nome do País associados (de acordo com DimGeography). Seu SELECT final deve conter apenas as seguintes colunas: StoreKey, StoreName, EmployeeCount, ContinentName e RegionCountryName. Utilize o LEFT JOIN neste exercício.

```sql
SELECT TOP (10) * FROM DimStore
SELECT TOP (10) * FROM DimGeography
SELECT COUNT(*) FROM DimStore
SELECT COUNT(*) FROM DimGeography

SELECT
	StoreKey,
	StoreName,
	EmployeeCount,
	ContinentName,
	RegionCountryName
FROM 
	DimStore
LEFT JOIN DimGeography
	ON DimStore.GeographyKey = DimGeography.GeographyKey
-- LEFT: 306 linhas.
-- INNER: 306 linhas.
```


### Aula 22: Resolução Exercício 4
- Complementa a tabela DimProduct com a informação de ProductCategoryDescription. Utilize o LEFT JOIN e retorne em seu SELECT apenas as 5 colunas que considerar mais relevantes.

```sql
SELECT * FROM DimProduct
SELECT * FROM DimProductCategory
SELECT * FROM DimProductSubcategory

SELECT
	ProductKey,
	ProductName,
	DimProduct.ProductSubcategoryKey,
	ProductSubcategoryName,
	ProductCategoryDescription
FROM 
	DimProduct
LEFT JOIN DimProductSubcategory
	ON DimProduct.ProductSubcategoryKey = DimProductSubcategory.ProductSubcategoryKey
		LEFT JOIN DimProductCategory
			on DimProductCategory.ProductCategoryKey = DimProductSubcategory.ProductCategoryKey
```


### Aula 23: Resolução Exercício 5
- A tabela FactStrategyPlan resume o planejamento estratégico da empresa. Cada linha representa um montante destinado a uma determinada AccountKey.
- a) Faça um SELECT das 100 primeiras linhas de FactStrategyPlan para reconhecer a tabela.

```sql
SELECT TOP(5)* FROM FactStrategyPlan
SELECT TOP(5)* FROM DimAccount
```

- b) Faça um INNER JOIN para criar uma tabela contendo o AccountName para cada AccountKey da tabela FactStrategyPlan. O seu SELECT final deve conter as colunas:
	• StrategyPlanKey
	• DateKey
	• AccountName
	• Amount

```sql
SELECT TOP(10)
	StrategyPlanKey,
	Datekey,
	AccountName,
	Amount
FROM
	FactStrategyPlan
INNER JOIN DimAccount
	ON FactStrategyPlan.AccountKey = DimAccount.AccountKey
```


### Aula 24: Resolução Exercício 6
- Vamos continuar analisando a tabela FactStrategyPlan. Além da coluna AccountKey que identifica o tipo de conta, há também uma outra coluna chamada ScenarioKey. Essa coluna possui a numeração que identifica o tipo de cenário: Real, Orçado e Previsão. Faça um INNER JOIN para criar uma tabela contendo o ScenarioName para cada ScenarioKey da tabela FactStrategyPlan. O seu SELECT final deve conter as colunas:
	• StrategyPlanKey
	• DateKey
	• ScenarioName
	• Amount

```sql
SELECT TOP(5)* FROM FactStrategyPlan
SELECT TOP(5)* FROM DimScenario

SELECT TOP(10)
	StrategyPlanKey,
	Datekey,
	ScenarioName,
	Amount
FROM
	FactStrategyPlan
INNER JOIN DimScenario
	ON FactStrategyPlan.ScenarioKey = DimScenario.ScenarioKey
```


### Aula 25: Resolução Exercício 7
- Algumas subcategorias não possuem nenhum exemplar de produto. Identifique que subcategorias são essas.

```sql
SELECT TOP(5)* FROM DimProductSubcategory
SELECT TOP(5)* FROM DimProduct

SELECT
	ProductSubcategoryName,
	ProductName
FROM 
	DimProductSubcategory
LEFT JOIN DimProduct
	ON DimProductSubcategory.ProductSubcategoryKey = DimProduct.ProductSubcategoryKey
WHERE ProductName IS NULL
```


### Aula 26: Resolução Exercício 8
- A tabela abaixo mostra a combinação entre Marca e Canal de Venda, para as marcas Contoso, Fabrikam e Litware. Crie um código SQL para chegar no mesmo resultado.
![image](https://github.com/user-attachments/assets/0ed0a4cc-d518-4ca8-82f9-ac18ec105033)

```sql
SELECT TOP(5)* FROM FactSales
SELECT * FROM DimChannel
SELECT TOP(5)* FROM DimProduct

SELECT
	DISTINCT BrandName,
	ChannelName
FROM
	DimProduct CROSS JOIN DimChannel
WHERE BrandName IN ('Contoso', 'Fabrikam', 'Litware')
```


### Aula 27: Resolução Exercício 9
- Neste exercício, você deverá relacionar as tabelas FactOnlineSales com DimPromotion. Identifique a coluna que as duas tabelas têm em comum e utilize-a para criar esse
relacionamento. A sua consulta deve considerar apenas as linhas de vendas referentes a produtos com desconto (PromotionName <> ‘No Discount’). Além disso, você deverá ordenar essa tabela de acordo com a coluna DateKey, em ordem crescente. Retorne uma tabela contendo as seguintes colunas:
	• OnlineSalesKey
	• DateKey
	• PromotionName
	• SalesAmount

```sql
SELECT TOP(5)* FROM FactOnlineSales
SELECT TOP(5)* FROM DimPromotion

SELECT TOP(10)
	OnlineSalesKey,
	DateKey,
	PromotionName,
	SalesAmount
FROM
	FactOnlineSales
INNER JOIN DimPromotion
	ON FactOnlineSales.PromotionKey = DimPromotion.PromotionKey
WHERE PromotionName <> 'No Discount'
ORDER BY DateKey
```


### Aula 28: Resolução Exercício 10
- A tabela abaixo é resultado de um Join entre a tabela FactSales e as tabelas: DimChannel, DimStore e DimProduct. Recrie esta consulta e classifique em ordem decrescente de acordo com SalesAmount
![image](https://github.com/user-attachments/assets/6105fd93-2a6d-477a-84f7-27baf17c6f7a)


```sql
SELECT TOP(5)* FROM FactSales -- saleskey, storekey, channelkey, productkey
SELECT TOP(5)* FROM DimChannel -- channelname, channelkey
SELECT TOP(5)* FROM DimStore -- storename, storekey
SELECT TOP(5)* FROM DimProduct -- productname, product key

SELECT TOP(5)
	SalesKey,
	ChannelName,
	StoreName,
	ProductName,
	SalesAmount
FROM FactSales
INNER JOIN DimChannel
	ON FactSales.channelKey = DimChannel.ChannelKey
INNER JOIN DimStore
	ON FactSales.StoreKey = DimStore.StoreKey
INNER JOIN DimProduct
	ON FactSales.ProductKey = DimProduct.ProductKey
ORDER BY SalesAmount DESC
```


----------------
## Módulo 9: Group By + Joins - Aplicações

### 1. Group By mais Inner Join
- a) Faça um resumo da quantidade vendida (Sales Quantity) de acordo com o nome do canal de vendas (ChannelName). Você deve ordenar a tabela final de acordo com SalesQuantity, em ordem decrescente.

```sql
SELECT TOP(100) * FROM FactSales
SELECT TOP(100) * FROM DimChannel

SELECT
	ChannelName AS 'Nome do canal',
	SUM(SalesQuantity) AS 'Total vendido'
FROM
	DimChannel
INNER JOIN FactSales
	ON DimChannel.ChannelKey = FactSales.channelKey
GROUP BY ChannelName
ORDER BY SUM(SalesQuantity) DESC
```

- b) Faça um agrupamento mostrando a quantidade total vendida (Sales Quantity) e quantidade total devolvida (Return Quantity) de acordo com o nome das lojas
(StoreName).

```sql
SELECT TOP(100) * FROM FactSales
SELECT TOP(100) * FROM DimStore

SELECT
	StoreName AS 'Nome do canal',
	SUM(SalesQuantity) AS 'Total vendido',
	SUM(ReturnQuantity) AS 'Total devolvido'
FROM
	DimStore
INNER JOIN FactSales
	ON DimStore.StoreKey = FactSales.StoreKey
GROUP BY StoreName
ORDER BY SUM(ReturnQuantity) DESC
```

- c) Faça um resumo do valor total vendido (Sales Amount) para cada mês (CalendarMonthLabel) e ano (CalendarYear).

```sql
SELECT TOP(100) * FROM FactSales
SELECT TOP(100) * FROM DimDate

-- Total vendido para cada mês
SELECT
	CalendarMonthLabel AS 'Mês',
	CalendarYear AS 'Ano',
	SUM(SalesAmount) AS 'Total vendido'
FROM
	DimDate
LEFT JOIN FactSales
	ON DimDate.Datekey = FactSales.DateKey
GROUP BY CalendarMonthLabel, CalendarYear, CalendarMonth
ORDER BY CalendarMonth
```


## Group By mais Inner Join - Fixação 1
-  Você precisa fazer uma análise de vendas por produtos. O objetivo final é descobrir o valor total vendido (SalesQuantity) por produto.
- a) Descubra qual é a cor de produto que mais é vendida (de acordo com SalesQuantity).

```sql
SELECT TOP(100) * FROM FactSales
SELECT TOP(100) * FROM DimProduct

SELECT
	ColorName AS 'Cor',
	SUM(SalesAmount) AS 'Total vendido'
FROM
	FactSales
INNER JOIN DimProduct
	ON FactSales.ProductKey = DimProduct.ProductKey
GROUP BY ColorName
ORDER BY SUM(SalesQuantity) DESC
```

- b) Quantas cores tiveram uma quantidade vendida acima de 3.000.000.

```sql
SELECT DISTINCT
	ColorName AS 'Cor',
	SUM(SalesQuantity) AS 'Total vendido'
FROM
	FactSales
INNER JOIN DimProduct
	ON FactSales.ProductKey = DimProduct.ProductKey
GROUP BY ColorName
HAVING SUM(SalesQuantity) > 3000000
ORDER BY SUM(SalesQuantity) DESC
```


### Group By mais Inner Join - Fixação 2
- Crie um agrupamento de quantidade vendida (SalesQuantity) por categoria do produto (ProductCategoryName). Obs: Você precisará fazer mais de 1 INNER JOIN, dado que a relação entre FactSales e DimProductCategory não é direta.

```sql
SELECT TOP(100) * FROM FactSales
SELECT TOP(100) * FROM DimProductCategory
SELECT TOP(100) * FROM DimProductSubcategory
SELECT TOP(100) * FROM DimProduct

SELECT
	ProductCategoryName AS 'Categoria do produto',
	SUM(SalesQuantity) AS 'Total vendido'
FROM
	FactSales
INNER JOIN DimProduct
	ON FactSales.ProductKey = DimProduct.ProductKey
		INNER JOIN DimProductSubcategory
			ON DimProduct.ProductSubcategoryKey = DimProductSubcategory.ProductSubcategoryKey
				INNER JOIN DimProductCategory
					ON DimProductCategory.ProductCategoryKey = DimProductSubcategory.ProductCategoryKey
GROUP BY ProductCategoryName
```


### Group By mais Inner Join - Fixação 3
-  a) Você deve fazer uma consulta à tabela FactOnlineSales e descobrir qual é o nome completo do cliente que mais realizou compras online (de acordo com a coluna SalesQuantity).

```sql
SELECT TOP(100) * FROM FactOnlineSales
SELECT TOP(100) * FROM DimCustomer
SELECT TOP(100) * FROM DimProduct

SELECT
	DimCustomer.CustomerKey,
	FirstName,
	LastName,
	SUM(SalesQuantity) AS 'Qtd. vendida'
FROM
	FactOnlineSales
INNER JOIN DimCustomer
	ON FactOnlineSales.CustomerKey = DimCustomer.CustomerKey
WHERE CustomerType = 'Person'
GROUP BY FirstName, LastName, DimCustomer.CustomerKey
ORDER BY SUM(SalesQuantity) DESC
```

- b) Feito isso, faça um agrupamento de produtos e descubra quais foram os top 10 produtos mais comprados pelo cliente da letra a, considerando o nome do produto.

```sql
SELECT TOP(10)
	FirstName AS 'Nome cliente', 
	ProductName AS 'Nome do produto',
	SUM(SalesQuantity) AS 'Qtd. comprada'
FROM
	FactOnlineSales
INNER JOIN DimCustomer
	ON FactOnlineSales.CustomerKey = DimCustomer.CustomerKey
		INNER JOIN DimProduct
			ON DimProduct.ProductKey = FactOnlineSales.ProductKey
WHERE DimCustomer.CustomerKey = '7665'
GROUP BY FirstName, ProductName
ORDER BY SUM(SalesQuantity) DESC
```


### Group By mais Inner Join - Fixação 4
- . Faça um resumo mostrando o total de produtos comprados (Sales Quantity) de acordo com o sexo dos clientes.

```sql
SELECT TOP(100) * FROM FactOnlineSales
SELECT TOP(100) * FROM DimCustomer
SELECT TOP(100) * FROM DimProduct

SELECT
	Gender AS 'Gênero',
	SUM(SalesQuantity) AS 'Qtd. comprada'
FROM
	FactOnlineSales
INNER JOIN DimCustomer
	ON FactOnlineSales.CustomerKey = DimCustomer.CustomerKey
WHERE CustomerType = 'Person'
GROUP BY Gender
```


### Group By mais Inner Join - Fixação 5
- Faça uma tabela resumo mostrando a taxa de câmbio média de acordo com cada CurrencyDescription. A tabela final deve conter apenas taxas entre 10 e 100.

```sql
SELECT TOP(10) * FROM FactExchangeRate
SELECT TOP(10) * FROM DimCurrency

SELECT
	CurrencyDescription,
	AVG(AverageRate) AS 'Taxa de câmbio média'
FROM
	FactExchangeRate
INNER JOIN DimCurrency
	ON FactExchangeRate.CurrencyKey = DimCurrency.CurrencyKey
GROUP BY CurrencyDescription
HAVING AVG(AverageRate) BETWEEN 10 AND 100
```


### Group By mais Inner Join - Fixação 6
- Calcule a SOMA TOTAL de AMOUNT referente à tabela FactStrategyPlan destinado aos cenários: Actual e Budget. Dica: A tabela DimScenario será importante para esse exercício.

```sql
SELECT TOP(10) * FROM FactStrategyPlan
SELECT TOP(10) * FROM DimScenario

SELECT
	ScenarioName AS 'Cenário',
	SUM(Amount) AS 'Valor total'
FROM
	FactStrategyPlan
INNER JOIN DimScenario
	ON FactStrategyPlan.ScenarioKey = DimScenario.ScenarioKey
WHERE ScenarioName IN ('Actual', 'Budget')
GROUP BY ScenarioName
```


### Group By mais Inner Join - Fixação 7
- Calcule a SOMA TOTAL de AMOUNT referente à tabela FactStrategyPlan destinado aos cenários: Actual e Budget. Dica: A tabela DimScenario será importante para esse exercício.

```sql
SELECT TOP(10) * FROM FactStrategyPlan
SELECT TOP(10) * FROM DimScenario

SELECT
	ScenarioName AS 'Cenário',
	SUM(Amount) AS 'Valor total'
FROM
	FactStrategyPlan
INNER JOIN DimScenario
	ON FactStrategyPlan.ScenarioKey = DimScenario.ScenarioKey
WHERE ScenarioName IN ('Actual', 'Budget')
GROUP BY ScenarioName
```


### Group By mais Inner Join - Fixação 8
- Faça uma tabela resumo mostrando o resultado do planejamento estratégico por ano.

```sql
SELECT TOP(10) * FROM FactStrategyPlan
SELECT TOP(10) * FROM DimDate

SELECT
	CalendarYear AS 'Ano',
	SUM(Amount) AS 'Valor total'
FROM
	FactStrategyPlan
INNER JOIN DimDate
	ON FactStrategyPlan.Datekey = DimDate.Datekey
GROUP BY CalendarYear
```


### Group By mais Inner Join - Fixação 9
- Faça um agrupamento de quantidade de produtos por ProductSubcategoryName. Leve em consideração em sua análise apenas a marca Contoso e a cor Silver.

```sql
SELECT TOP(10) * FROM DimProduct
SELECT TOP(10) * FROM DimProductSubcategory

SELECT
	ProductSubcategoryName,
	COUNT(ProductSubcategoryName) AS 'Qtd. produtos'
FROM
	DimProductSubcategory
INNER JOIN DimProduct
	ON DimProductSubcategory.ProductSubcategoryKey = DimProduct.ProductSubcategoryKey
WHERE BrandName = 'Contoso' AND ColorName = 'Silver'
GROUP BY ProductSubcategoryName
ORDER BY COUNT(ProductSubcategoryName) DESC
```


### Group By mais Inner Join - Fixação 9
- Faça um agrupamento duplo de quantidade de produtos por BrandName e ProductSubcategoryName. A tabela final deverá ser ordenada de acordo com a coluna BrandName.

```sql
SELECT TOP(10) * FROM DimProduct
SELECT TOP(10) * FROM DimProductSubcategory

SELECT
	BrandName AS 'Marca',
	ProductSubcategoryName,
	COUNT(ProductSubcategoryName) AS 'Qtd. produtos'
FROM
	DimProductSubcategory
INNER JOIN DimProduct
	ON DimProductSubcategory.ProductSubcategoryKey = DimProduct.ProductSubcategoryKey
GROUP BY BrandName, ProductSubcategoryName
ORDER BY BrandName
```


------------
## Módulo 10: Variáveis

### Aula 2: Tipos de Dados

```sql
/* 
Tipos de dados

O tipo de dado é a maneira como o SQL consegue diferenciar cada valor dentro de um banco de dados.

a) Inteiro 
Exemplos:
1, 100, 569

Como o SQL entende um número inteiro: INT


b) Decimal
Exemplos:
10.33, 90.91, 410.787

Como o SQL entende um número decimal: FLOAT
Como o SQL entende um número decimal: DECIMAL(N, M)

N é a quantidade de dígitos que o númeto pode ter, incluindo casas decimais
M é o número máximo de casas decimais


c) Texto/String
Exemplos:
'Carla', 'Motorola', 'Pastel', '44'

Como o SQL entende um texto: VARCHAR(N)

N é o número de caracteres que o texto pode ter


d) Data
Exemplos:
'01/01/2021', '23/03/2021'

Como o SQL entende uma data/hora: DATETIME
Como o SQL entende uma data: DATE

*/
```

### Aula 3: Operações Básicas

```sql
-- Operações básicas

SELECT 10 AS 'Número'

SELECT 'Marcus' AS 'Nome'

SELECT '21/06/2021' AS 'Data'

-- Operações com números

SELECT 10+20
SELECT 20-5
SELECT 31*40
SELECT 431.0/23

-- Operações com textos

SELECT 'SQL' + ' ' + 'Impressionador'

-- Operações com datas

SELECT '21/03/2021' + 1
```


### Aula 4: SQL_VARIANT_PROPERTY - Identificando o tipo de um dado

```sql
SELECT 10 AS 'Número'
SELECT 49.50 AS 'Decimal'
SELECT 'Marcus' AS 'Nome'
SELECT '20/06/2021' AS 'Data'

SELECT SQL_VARIANT_PROPERTY(10, 'BaseType')
SELECT SQL_VARIANT_PROPERTY(49.50, 'BaseType')
SELECT SQL_VARIANT_PROPERTY('Marcus', 'BaseType')
SELECT SQL_VARIANT_PROPERTY('20/06/2021', 'BaseType')
```


### Aula 5: CAST - Especificando o tipo de um dado

```sql
-- 1) CAST: Função para especificar o tipo dos valores.
-- int: inteiro, float: decimal, varchar: string/texto, datetime: data e hora

SELECT CAST(21.45 AS int)

SELECT CAST(21.45 AS float)

SELECT CAST(18.7 AS varchar)

SELECT CAST('15.6' AS float)

SELECT CAST('31/05/2014' AS datetime)


-- Exemplo 1: Crie uma consulta juntando o texto 'O preço do produto é: ' com o valor 30.99

SELECT 'O preço do produto é: ' + CAST(30.99 AS VARCHAR(30))

-- Exemplo 2: Adicione 1 dia à data '20/06/2021'

SELECT CAST('20/06/2021' AS DATETIME) + 1
```


### Aula 6: FORMAT - Formatação de dados personalizada

```sql
--FORMAT: Função para formatação de valores no SQL

-- a) Numéricos:
SELECT FORMAT(1000, 'N')
SELECT FORMAT(1000, 'G')

-- b) Personalizados:
SELECT FORMAT(123456789, '###-##-####')

-- c) Data:
SELECT FORMAT(CAST('21/03/2021' AS DATETIME), 'dd/MM/yyyy')


-- SQL_VARIANT_PROPERTY
SELECT SQL_VARIANT_PROPERTY('31/05/2014', 'BaseType')
SELECT SQL_VARIANT_PROPERTY(CAST('31/05/2014' AS datetime), 'BaseType')
```


### Aula 7: ROUND, FLOOR e CEILING - Funções de Arredondamento

```sql
-- Operações com números

SELECT 10+20
SELECT 20-5
SELECT 31*40
SELECT 431.0/23

-- ROUND

SELECT ROUND(18.739130, 2)

-- ROUND (Truncar)

SELECT ROUND(18.739130, 2, 1)

-- FLOOR

SELECT FLOOR(18.739130)

-- CEILING

SELECT CEILING(18.739130)
```



### Aula 8: DECLARE e SET Declarando uma variável

```sql
/* 
Declarando Variáveis 

1) O que é uma variável?
Uma variável é um objeto que armazena o valor de um dado.

2. Estrutura

DECLARE @var tipo
SET @var = valor


DECLARE @var1 INT, @var2 INT,
	 @texto VARCHAR(MAX),
	 @data DATETIME
	
SET @var1 = 10
SET @var1 = 45
SET @texto = 'Um texto qualquer'
SET @data = '18/02/2021'

*/

SELECT 100 * 8.99 AS 'faturamento'

DECLARE @quantidade AS int, @preco AS float
SET @quantidade = 100
SET @preco = 8.99

SELECT @quantidade * @preco AS 'faturamento'

-- Exemplo 1: Declare uma variável chamada 'idade' e armazene o valor 30

DECLARE @idade AS INT

SET @idade = 30

SELECT @idade

-- Exemplo 2: Declare uma variável chamada 'preco' e armazene o valor 10.89

DECLARE @preco AS float
SET @preco = 10.89
SELECT @preco

DECLARE @preco2 AS decimal(5, 2)
SET @preco2 = 10.89
SELECT @preco2



-- Exemplo 3: Declare uma variável chamada 'nome' e armazene o valor 'Mateus'

DECLARE @nome AS varchar(50)
SET @nome = 'Mateus'
SELECT @nome

-- Exemplo 4: Declare uma variável chamada 'data' e armazene a data de hoje.

DECLARE @data AS datetime
SET @data = '2021-10-28'
SELECT @data

SELECT DAY(@data)
```


### Aula 11: Utilizando uma variável em uma consulta (Parte 1)

```sql
-- Aplique um desconto de 10% em todos os preços dos produtos. Sua consulta final deve conter as colunas ProductKey, ProductName, UnitPrice e Preço com Desconto. 

DECLARE @varDesconto FLOAT
SET @varDesconto = 0.1

SELECT 
	ProductKey AS 'ID',
	ProductName AS 'Nome do Produto',
	UnitPrice AS 'Preço',
	UnitPrice * (1 - @varDesconto) AS 'Preço com Desconto'
FROM
	DimProduct
```


### Aula 12: Utilizando uma variável em uma consulta (Parte 2)

```sql
-- Crie uma variável de data para otimizar a consulta abaixo. 

DECLARE @varData DATETIME
SET @varData = '01/01/1980'

SELECT 
	FirstName AS 'Nome',
	LastName AS 'Sobrenome',
	BirthDate AS 'Nascimento',
	'Cliente' AS 'Tipo'
FROM	
	DimCustomer
WHERE BirthDate >= @varData

UNION

SELECT 
	FirstName AS 'Nome',
	LastName AS 'Sobrenome',
	BirthDate AS 'Nascimento',
	'Funcionário' AS 'Tipo'
FROM	
	DimEmployee
WHERE BirthDate >= @varData
ORDER BY Nascimento
```


### Aula 13: Armazenando o resultado de um SELECT em uma variável

```sql
-- Exemplo 1: Crie uma variável para armazenar a quantidade total de funcionários da tabela DimEmployee.

DECLARE @varTotalFuncionarios INT
SET @varTotalFuncionarios = (SELECT COUNT(*) FROM DimEmployee)
SELECT @varTotalFuncionarios


-- Exemplo 2: Crie uma variável para armazenar a quantidade total de lojas com o status Off.

DECLARE @varLojasOff INT
SET @varLojasOff = (SELECT COUNT(*) FROM DimStore WHERE Status = 'Off')
SELECT @varLojasOff
```


### Aula 14: PRINT - Printando uma mensagem na tela

```sql
-- Exemplo 1: Printe na tela a quantidade de lojas On e a quantidade  de lojas Off da tabela DimStore. Utilize variáveis para isso.

DECLARE @varLojasOn INT, @varLojasOff INT
SET @varLojasOn = (SELECT COUNT(*) FROM DimStore WHERE Status = 'On')
SET @varLojasOff = (SELECT COUNT(*) FROM DimStore WHERE Status = 'Off')

SELECT @varLojasOn AS 'Lojas Abertas', @varLojasOff AS 'Lojas Fechadas'

PRINT 'O total de lojas abertas é de ' + CAST(@varLojasOn AS VARCHAR(30))
PRINT 'O total de lojas fechadas é de ' + CAST(@varLojasOff AS VARCHAR(30))
```


### Aula 15: Armazenando em uma variável um registro de uma consulta

```sql
-- Exemplo 1: Qual é o nome do produto que teve a maior quantidade vendida EM UMA ÚNICA VENDA da tabela FactSales?

DECLARE @varProdutoMaisVendido INT
DECLARE @varTotalMaisVendido INT

SELECT TOP(1)
	@varProdutoMaisVendido = ProductKey,
	@varTotalMaisVendido = SalesQuantity
FROM
	FactSales
ORDER BY SalesQuantity DESC

PRINT @varProdutoMaisVendido
PRINT @varTotalMaisVendido

SELECT
	ProductKey,
	ProductName
FROM
	DimProduct
WHERE ProductKey = @varProdutoMaisVendido
```


### Aula 16: Acumulando valores dentro de uma variável

```sql
-- Exemplo 1: Retorne uma lista com os nomes dos funcionários do departamento de Marketing
DECLARE @ListaNomes VARCHAR(MAX)
SET @ListaNomes = ''

SELECT
	@ListaNomes = @ListaNomes + FirstName + ', ' + CHAR(10)
FROM
	DimEmployee
WHERE DepartmentName = 'Marketing'

PRINT LEFT(@ListaNomes, DATALENGTH(@ListaNomes) - 3)
```


### Aula 17: Variáveis Globais

```sql
SELECT @@SERVERNAME
SELECT @@VERSION

SELECT * FROM DimProduct
SELECT @@ROWCOUNT
```


### Aula 19: Resolução Exercício 1
- Declare 4 variáveis inteiras. Atribua os seguintes valores a elas:
	- valor1 = 10
	- valor2 = 5
	- valor3 = 34
	- valor4 = 7
- a) Crie uma nova variável para armazenar o resultado da soma entre valor1 e valor2. Chame essa variável de soma.

```sql
DECLARE @valor1 INT = 10,
	@valor2 INT = 5,
	@valor3 INT = 34,
	@valor4 INT = 7

DECLARE @soma INT = (SELECT @valor1 + @valor2)
SELECT @soma
```

- b) Crie uma nova variável para armazenar o resultado da subtração entre valor3 e valor 4. Chame essa variável de subtracao.

```sql
DECLARE @valor1 INT = 10,
	@valor2 INT = 5,
	@valor3 INT = 34,
	@valor4 INT = 7

DECLARE @subtracao INT = (SELECT @valor3 - @valor4)
SELECT @subtracao
```

- c) Crie uma nova variável para armazenar o resultado da multiplicação entre o valor 1 e o valor4. Chame essa variável de multiplicacao.

```sql
DECLARE @valor1 INT = 10,
	@valor2 INT = 5,
	@valor3 INT = 34,
	@valor4 INT = 7

DECLARE @multiplicacao INT = (SELECT @valor1 * @valor4)
SELECT @multiplicacao
```

- d) Crie uma nova variável para armazenar o resultado da divisão do valor3 pelo valor4. Chame essa variável de divisao. Obs: O resultado deverá estar em decimal, e não em inteiro.

```sql
DECLARE @valor1 INT = 10,
	@valor2 INT = 5,
	@valor3 INT = 34,
	@valor4 INT = 7

DECLARE @divisao FLOAT = (SELECT CAST(@valor3 AS FLOAT) / CAST(@valor4 AS FLOAT))
SELECT CAST(@divisao AS FLOAT)
```

- e) Arredonde o resultado da letra d) para 2 casas decimais.

```sql
DECLARE @valor1 INT = 10,
	@valor2 INT = 5,
	@valor3 INT = 34,
	@valor4 INT = 7

DECLARE @divisao FLOAT = (SELECT CAST(@valor3 AS FLOAT) / CAST(@valor4 AS FLOAT))
SELECT ROUND(CAST(@divisao AS FLOAT), 2)
```


### Aula 20: Resolução Exercício 2
- Para cada declaração das variáveis abaixo, atenção em relação ao tipo de dado que deverá ser especificado.
- a) Declare uma variável chamada ‘produto’ e atribua o valor de ‘Celular’.

```sql
DECLARE @produto VARCHAR(30) = 'Celular'
SELECT @produto
```

- b) Declare uma variável chamada ‘quantidade’ e atribua o valor de 12.

```sql
DECLARE @quantidade INT = 12
SELECT @quantidade
```

- c) Declare uma variável chamada ‘preco’ e atribua o valor 9.99.

```sql
DECLARE @preco FLOAT = 9.99
SELECT @preco
```

- d) Declare uma variável chamada ‘faturamento’ e atribua o resultado da multiplicação entre ‘quantidade’ e ‘preco’.

```sql
DECLARE @faturamento FLOAT = (SELECT @quantidade * @preco)
SELECT @faturamento
```

- e) Visualize o resultado dessas 4 variáveis em uma única consulta, por meio do SELECT.

```sql
SELECT @produto, @quantidade, @preco, @quantidade
```


### Aula 21: Resolução Exercício 3
- Você é responsável por gerenciar um banco de dados onde são recebidos dados externos de usuários. Em resumo, esses dados são:
	- Nome do usuário
	- Data de nascimento
	- Quantidade de pets que aquele usuário possui
- Você precisará criar um código em SQL capaz de juntar as informações fornecidas por este usuário. Para simular estes dados, crie 3 variáveis, chamadas: nome, data_nascimento e num_pets. Você deverá armazenar os valores ‘André’, ‘10/02/1998’ e 2, respectivamente. O resultado final a ser alcançado é mostrado no print abaixo:
![image](https://github.com/user-attachments/assets/81a39dbe-535d-490c-92f9-9842acf0b724)
- Dica: você precisará utilizar as funções CAST e FORMAT para chegar no resultado.

```sql
DECLARE @nome VARCHAR(30) = 'André',
		@data_nascimento DATETIME = '10/02/1998',
		@num_pets INT = 2

SELECT 'Meu nome é ' + @nome + ', nasci em ' + 
		FORMAT(@data_nascimento, 'dd/MM/yyyy') + ' e tenho ' + 
		CAST(@num_pets AS VARCHAR(30)) + ' pets.'
```


### Aula 22: Resolução Exercício 4
- Você acabou de ser promovido e o seu papel será realizar um controle de qualidade sobre as lojas da empresa. A primeira informação que é passada a você é que o ano de 2008 foi bem complicado para a empresa, pois foi quando duas das principais lojas fecharam. O seu primeiro desafio é descobrir o nome dessas lojas que fecharam no ano de 2008, para que você possa entender o motivo e mapear planos de ação para evitar que outras lojas importantes tomem o mesmo caminho. O seu resultado deverá estar estruturado em uma frase, com a seguinte estrutura: ‘As lojas fechadas no ano de 2008 foram: ’ + nome_das_lojas. Obs: utilize o comando PRINT (e não o SELECT!) para mostrar o resultado.

```sql
SELECT * FROM DimStore
SELECT * FROM DimProductSubcategory

SELECT StoreName, CloseDate FROM DimStore
WHERE FORMAT(CloseDate, 'yyyy') = 2008

DECLARE @varLojas VARCHAR(50)
SET @varLojas = ''

SELECT 
	@varLojas = @varLojas + StoreName + ', '
FROM
	DimStore
WHERE FORMAT(CloseDate, 'yyyy') = 2008

PRINT 'As lojas fechadas no ano de 2008 foram: ' + @varLojas
```


### Aula 23: Resolução Exercício 5
- Você precisa criar uma consulta para mostrar a lista de produtos da tabela DimProduct para uma subcategoria específica: ‘Lamps’. Utilize o conceito de variáveis para chegar neste resultado.

```sql
SELECT * FROM DimProduct
SELECT * FROM DimProductSubcategory

DECLARE	@idSubcategoria INT
DECLARE @subcategoria VARCHAR(20)

SET @subcategoria = 'Lamps'
SET @idSubcategoria = (SELECT ProductSubcategoryKey FROM DimProductSubcategory WHERE ProductSubcategoryName = @subcategoria)

SELECT
	*
FROM
	DimProduct
WHERE ProductSubcategoryKey = @idSubcategoria
```


-------------
## Módulo 11: 

### Aula 2: LEN e DATALENGTH

```sql
-- Exemplo: Descubra a quantidade de caracteres da palavra 'SQL Hashtag'

SELECT
	LEN('SQL Hashtag') AS 'Len',
	DATALENGTH('SQL Hashtag') AS 'Datalength'
```


### Aula 3: CONCAT

```sql
-- CONCAT ---> Permite juntar mais de um texto em uma única palavra
-- Exemplo: Faça uma consulta à tabela DimCustomer onde seja possível visualizar o nome completo de cada cliente.

SELECT
	FirstName AS 'Nome',
	LastName AS 'Sobrenome',
	EmailAddress AS 'E-mail',
	CONCAT(FirstName, ' ', LastName) AS 'Nome Completo'
FROM
	DimCustomer
```


### Aula 4: LEFT e RIGHT

```sql
-- LEFT ---> Extrai uma determinada quantidade de caracteres de um texto, da esquerda para a direita
-- RIGHT ---> Extrai uma determinada quantidade de caracteres de um texto, da direita para a esquerda
-- Exemplo: Faça uma consulta à tabela DimProduct e divida a coluna de StyleName em 2 partes

SELECT * FROM DimProduct
SELECT
	ProductName AS 'Produto',
	UnitPrice AS 'Preço',
	LEFT(StyleName, 7) AS 'Cod 1',
	RIGHT(StyleName, 7) AS 'Cod 2'
FROM
	DimProduct
```


### Aula 5 e 6: REPLACE (Parte 1 e 2)

```sql
-- REPLACE ---> Substitui um determinado texto por outro texto

-- Exemplo: Crie uma consulta a partir de DimCustomer onde você retorna o Nome Completo dos Clientes, a coluna de Sexo (Abrev) e uma outra coluna de Sexo substituindo M por Masculino e F por Feminino

SELECT * FROM DimCustomer
SELECT
	CONCAT(FirstName, ' ', LastName) AS 'Nome Completo',
	Gender AS 'Sexo (Abrev)',
	REPLACE(REPLACE(Gender, 'M', 'Masculino'), 'F', 'Feminino') AS 'Sexo (Extenso)'
FROM
	DimCustomer
```


### Aula 7: TRANSLATE e STUFF

```sql
-- TRANSLATE e STUFF: Outras funções de substituição

SELECT TRANSLATE('3*[2+1]/{8-4}', '[]{}', '()()')

SELECT TRANSLATE('ABCD-490123', 'ABCD', 'WXYZ')

SELECT STUFF('VBA Impressionador', 1, 3, 'Excel')
```


### Aula 8: UPPER e LOWER

```sql
-- UPPER ---> Transforma um texto em maiúscula
-- LOWER ---> Transforma um texto em minúscula
-- Exemplo: Faça uma consulta à tabela DimCustomer e utilize as funções UPPER e LOWER na coluna de FirstName para observar o resultado

SELECT * FROM DimCustomer
SELECT
	UPPER(FirstName) AS 'NOME',
	LOWER(FirstName) AS 'nome',
	EmailAddress AS 'E-mail'
FROM
	DimCustomer
```


### Aula 9: FORMAT

```sql
--SELECT * FROM DimCustomer

-- Formatação de Data
SELECT 
	GETDATE() AS 'Data',
	FORMAT(GETDATE(),'dd/MMMM/yyyy','pt-br') AS 'Data Formatada'

-- Formatação de Número
SELECT 
	50123 AS 'Número',
	FORMAT(5123, '000000.00') AS 'Número Formatado'

-- Formatação de Moeda
SELECT 
	3670.5 AS 'Moeda',
	FORMAT(5670.5, 'R$####.00') AS 'Moeda Formatada'


-- Formatar as colunas de Data de Nascimento e Renda Anual da tabela DimCustomer, de acordo com as formatações aprendidas.

SELECT
	FirstName AS 'Nome',
	BirthDate AS 'Data de Nascimento',
	FORMAT(BirthDate, 'dd/MMMM/yyyy', 'pt-BR') AS 'Data Formatada',
	YearlyIncome AS 'Renda Anual',
	FORMAT(YearlyIncome, 'R$##,###.00') AS 'Renda Anual Formatada'
FROM
	DimCustomer
```


### Aula 10, 11 e 12: CHARINDEX e SUBSTRING

```sql
-- CHARINDEX: Descobre a posição de um determinado caractere dentro de um texto
-- SUBSTRING: Extrai alguns caracteres de dentro de um texto

SELECT CHARINDEX('Moreno', 'Raquel Moreno') AS 'Posição Sobrenome'

SELECT SUBSTRING('Raquel Moreno', 8, 6) AS 'Sobrenome'


SELECT 'Marcus Cavalcanti' AS 'Nome'

SELECT CHARINDEX(' ', 'Marcus Cavalcanti') AS 'Posição'

SELECT SUBSTRING('Marcus Cavalcanti', CHARINDEX(' ', 'Marcus Cavalcanti') + 1, 100) AS 'Sobrenome'
```


### Aula 13: TRIM, LTRIM e RTRIM

```sql
-- Funções para retirar espaços adicionais dentro de um texto
-- TRIM: Retira espaços adicionais à esquerda e à direita do texto
-- LTRIM: Retira espaços adicionais à esquerda do texto
-- RTRIM: Retira espaços adicionais à direita do texto

-- Utilize as funções acima no código '   ABC123   '

DECLARE @varCodigo VARCHAR(50)
SET @varCodigo = '   ABC123   '

SELECT
	TRIM(@varCodigo) AS 'Trim',
	LTRIM(@varCodigo) AS 'Ltrim',
	RTRIM(@varCodigo) AS 'Rtrim'

SELECT
	DATALENGTH(TRIM(@varCodigo)) AS 'Trim',
	DATALENGTH(LTRIM(@varCodigo)) AS 'Ltrim',
	DATALENGTH(RTRIM(@varCodigo)) AS 'Rtrim'
```


### Aula 14: DAY, MONTH, YEAR e DATEFROMPARTS

```sql
-- Utilize as funções DAY, MONTH e YEAR para descobrir o dia, mês e ano da data: 18/05/2020

DECLARE @varData DATETIME
SET @varData = '18/05/2020'

SELECT
	DAY(@varData) AS 'Dia',
	MONTH(@varData) AS 'Mês',
	YEAR(@varData) AS 'Ano'


-- Utilize a função DATEFROMPARTS para obter uma data a partir das informações de dia, mês e ano

DECLARE @varDia INT, @varMes INT, @varAno INT
SET @varDia = 29
SET @varMes = 12
SET @varAno = 2020

SELECT
	DATEFROMPARTS(@varAno, @varMes, @varDia) AS 'Data'
```


### Aula 15: GETDATE, SYSDATETIME, DATEPART e DATENAME

```sql
-- GETDATE: Retorna a data/hora atual do sistema
-- SYSDATETIME: Retorna a data/hora atual do sistema (mais preciso que a GETDATE)
-- DATENAME e DATEPART: Retornam informações (dia, mês, ano, semana, etc) de uma data

SELECT GETDATE()
SELECT SYSDATETIME()

-- DATENAME: Retorna o resultado em formato de TEXTO

DECLARE @varData DATETIME
SET @varData = GETDATE()
SELECT
	DATENAME(DAY, @varData) AS 'Dia',
	DATENAME(MONTH, @varData) AS 'Mês',
	DATENAME(YEAR, @varData) AS 'Ano',
	DATENAME(DAYOFYEAR, @varData) AS 'Dia do ano'

-- DATEPART: Retorna o resultado em formato de NÚMERO

DECLARE @varData DATETIME
SET @varData = GETDATE()
SELECT
	DATEPART(DAY, @varData) AS 'Dia',
	DATEPART(MONTH, @varData) AS 'Mês',
	DATEPART(YEAR, @varData) AS 'Ano',
	DATEPART(DAYOFYEAR, @varData) AS 'Dia do ano'

SELECT
	SQL_VARIANT_PROPERTY(DATENAME(DAY, @varData), 'BaseType'),
	SQL_VARIANT_PROPERTY(DATEPART(DAY, @varData), 'BaseType')
```


### Aula 16: DATEADD e DATEDIFF

```sql
-- DATEADD: Adiciona ou subtrai uma determinada quantidade de dias, meses ou anos a uma data
-- DATEDIFF: Calcula a diferença entre duas datas

DECLARE @varData1 DATETIME, @varData2 DATETIME, @varData3 DATETIME
SET @varData1 = '10/07/2020'
SET @varData2 = '05/03/2020'
SET @varData3 = '14/11/2021'

-- DATEADD
SELECT
	DATEADD(MONTH, -1, @varData1)

-- DATEDIFF
SELECT
	DATEDIFF(MONTH, @varData2, @varData3)
```


### Aula 18: Resolução Exercício 1
- Quando estamos manipulando tabelas, é importante pensar em como os dados serão apresentados em um relatório. Imagine os nomes dos produtos da tabela DimProduct. Os
textos são bem grandes e pode ser que mostrar os nomes completos dos produtos não seja a opção mais interessante, pois provavelmente não vão caber em um gráfico e a visualização ficará ruim.
- a) Seu gestor te pede para listar todos os produtos para que seja criado um gráfico para ser apresentado na reunião diária de equipe. Faça uma consulta à tabela DimProduct que retorne (1) o nome do produto e (2) a quantidade de caracteres que cada produto tem, e ordene essa tabela do produto com a maior quantidade de caracteres para a menor.

```sql
SELECT
	ProductName AS 'Nome do Produto',
	BrandName,
	ColorName,
	LEN(ProductName) AS 'Caracter Produto'
FROM
	DimProduct
ORDER BY LEN(ProductName) DESC
```

- b) Qual é a média de caracteres dos nomes dos produtos?

```sql
SELECT
	AVG(LEN(ProductName)) AS 'Média dos Caracteres'
FROM
	DimProduct
```

- c) Analise a estrutura dos nomes dos produtos e verifique se seria possível reduzir o tamanho do nome dos produtos. (Dica: existem informações redundantes nos nomes dos produtos? Seria possível substituí-las?)

```sql
SELECT * FROM DimProduct

SELECT
	BrandName,
	ColorName,
	ProductName AS 'Nome do Produto',
	SUBSTRING(
		LEFT(
			ProductName, 
			LEN(ProductName)-LEN(ColorName)-1
		),
		LEN(BrandName)+1,100
	) AS 'Nome do Produto Compacto'
FROm
	DimProduct

-- Teacher's solution
SELECT
	BrandName,
	ColorName,
	REPLACE(REPLACE(ProductName, BrandName, ''), ColorName, '') AS 'Nome do Produto Compacto'
FROm
	DimProduct
```

d) Qual é a média de caracteres nesse novo cenário?

```sql
SELECT
	AVG(LEN(
		SUBSTRING(
			LEFT(
				ProductName, 
				LEN(ProductName)-LEN(ColorName)-1),
			LEN(BrandName)+1,100
		)
	)) AS 'Media'
FROM
	DimProduct

-- Teacher's solution
SELECT
	AVG(LEN(REPLACE(REPLACE(ProductName, BrandName, ''), ColorName, ''))) AS 'Nome do Produto Compacto'
FROm
	DimProduct
```


### Aula 19: Resolução Exercício 2
- A coluna StyleName da tabela DimProduct possui alguns códigos identificados por números distintos, que vão de 0 até 9, como pode ser visto no exemplo abaixo.
![image](https://github.com/user-attachments/assets/0a90dd34-fab7-4cea-8d8a-47a4cbcbe64c)
- Porém, o setor de controle decidiu alterar a identificação do StyleName, e em vez de usar números, a ideia agora é passar a usar letras para substituir os números, conforme exemplo abaixo:
- 0 -> A, 1 -> B, 2 -> C, 3 -> D, 4 -> E, 5 -> F, 6 -> G, 7 -> H, 8 -> I, 9 - J
- É de sua responsabilidade alterar os números por letras na coluna StyleName da tabela DimProduct. Utilize uma função que permita fazer essas substituições de forma prática e rápida.

```sql
SELECT * FROM DimProduct

SELECT
	StyleName,
	TRANSLATE(StyleName, '0123456789', 'ABCDEFGHIJ') AS 'Nova StyleName'
FROM
	DimProduct
```


### Aula 20: Resolução Exercício 3
- O setor de TI está criando um sistema para acompanhamento individual de cada funcionário da empresa Contoso. Cada funcionário receberá um login e senha. O login de cada funcionário será o ID do e-mail, como no exemplo abaixo:
![image](https://github.com/user-attachments/assets/0ce3ac30-ba08-456a-920a-931ee9d4393d)
- Já a senha será o FirtName + o dia do ano em que o funcionário nasceu, em MAIÚSCULA. Por exemplo, o funcionário com E-mail: mark0@contoso.com e data de nascimento 15/01/1990 deverá ter a seguinte senha:
	- Login: mark0
	- Senha: MARK15
- O responsável pelo TI pediu a sua ajuda para retornar uma tabela contendo as seguintes colunas da tabela DimEmployee: Nome completo (FirstName + LastName), E-mail, ID do e-mail e Senha. Portanto, faça uma consulta à tabela DimProduct e retorne esse resultado.

```sql
SELECT * FROM DimEmployee

SELECT
	CONCAT(FirstName, ' ', LastName) AS 'Nome Completo',
	EmailAddress AS 'E-mail',
	LEFT(EmailAddress, CHARINDEX('@', EmailAddress)-1) AS 'ID do e-mail',
	CONCAT(UPPER(FirstName), DATENAME(DAY, BirthDate)) AS 'Senha'
FROM
	DimEmployee
```


### Aula 21: Resolução Exercício 4
- A tabela DimCustomer possui o primeiro registro de vendas no ano de 2001. Como forma de reconhecer os clientes que compraram nesse ano, o setor de Marketing solicitou a você que retornasse uma tabela com todos os clientes que fizeram a sua primeira compra neste ano para que seja enviado uma encomenda com um presente para cada um. Para fazer esse filtro, você pode utilizar a coluna DateFirstPurchase, que contém a informação da data da primeira compra de cada cliente na tabela DimCustomer. Você deverá retornar as colunas de FirstName, EmailAddress, AddressLine1 e DateFirstPurchase da tabela DimCustomer, considerando apenas os clientes que fizeram a primeira compra no ano de 2001.

```sql
SELECT * FROM DimCustomer

-- FORMAT
SELECT
	FirstName,
	EmailAddress,
	AddressLine1,
	DateFirstPurchase
FROM
	DimCustomer
WHERE FORMAT(DateFirstPurchase, 'yyyy') = 2001

-- YEAR
SELECT
	FirstName,
	EmailAddress,
	AddressLine1,
	DateFirstPurchase
FROM
	DimCustomer
WHERE YEAR(DateFirstPurchase) = 2001

-- DATENAME
SELECT
	FirstName,
	EmailAddress,
	AddressLine1,
	DateFirstPurchase
FROM
	DimCustomer
WHERE DATENAME(YEAR, DateFirstPurchase) = 2001

-- DATEPART
SELECT
	FirstName,
	EmailAddress,
	AddressLine1,
	DateFirstPurchase
FROM
	DimCustomer
WHERE DATEPART(YEAR, DateFirstPurchase) = 2001
```


### Aula 22: Resolução Exercício 5
- A tabela DimEmployee possui uma informação de data de contratação (HireDate). A área de RH, no entanto, precisa das informações dessas datas de forma separada em dia, mês e ano, pois será feita uma automatização para criação de um relatório de RH, e facilitaria muito se essas informações estivessem separadas em uma tabela. Você deverá realizar uma consulta à tabela DimEmployee e retornar uma tabela contendo as seguintes informações: FirstName, EmailAddress, HireDate, além das colunas de Dia, Mês e Ano de contratação. Obs1: A coluna de Mês deve conter o nome do mês por extenso, e não o número do mês. Obs2: Lembre-se de nomear cada uma dessas colunas em sua consulta para garantir que o entendimento de cada informação ficará 100% claro.

```sql
SELECT * FROM DimEmployee

-- FORMAT
SELECT
	FirstName AS 'Nome do Funcionário',
	EmailAddress AS 'E-mail',
	HireDate AS 'Data de contratação',
	FORMAT(HireDate, 'dd') AS 'Dia',
	FORMAT(HireDate, 'MMMM') AS 'Mês',
	FORMAT(HireDate, 'yyy') AS 'Ano'
FROM
	DimEmployee

-- DATENAME
SELECT
	FirstName AS 'Nome do Funcionário',
	EmailAddress AS 'E-mail',
	HireDate AS 'Data de contratação',
	DATENAME(DAY, HireDate) AS 'Dia',
	DATENAME(MONTH, HireDate) AS 'Mês',
	DATENAME(YEAR, HireDate) AS 'Ano'
FROM
	DimEmployee
```


### Aula 23: Resolução Exercício 6
-  Descubra qual é a loja que possui o maior tempo de atividade (em dias). Você deverá fazer essa consulta na tabela DimStore, e considerar a coluna OpenDate como referência para esse cálculo.

```sql
SELECT * FROM DimStore

SELECT TOP(1)
	StoreName AS 'Nome da Loja',
	DATEDIFF(DAY, OpenDate, GETDATE()) AS 'Dias Abertos'
FROM 
	DimStore
ORDER BY DATEDIFF(DAY, OpenDate, GETDATE()) DESC
```


------------
## Módulo 12: Funções Condicionais

### Aula 2: CASE WHEN... ELSE (Explicação)
- Determine a situação do aluno. Média >= 6: Aprovado. Caso contrário: Reprovado.

```sql
DECLARE @varNota FLOAT
SET @varNota = 7

SELECT
  CASE
    WHEN @varNota >= 6 THEN 'Aprovado'
    ELSE 'Reprovado'
  END AS 'Situação'
```

- A data de vencimento de um produto é no dia 10/03/2022. Faça um teste lógico para verificar se um produto passou da validade ou não.

```sql
DECLARE @varDataVencimento DATETIME, @varDataAtual DATETIME
SET @varDataVencimento = '10/03/2022'
SET @varDataAtual = '30/04/2020'

SELECT
  CASE
    WHEN @varDataAtual > @varDataVencimento THEN 'Produto vencido'
    ELSE 'Na validade'
  END AS 'Situação'
```

## Aula 3: CASE WHEN... ELSE (Exemplo)
- Faça um SELECT das colunas CustomerKey, FirstName e Gender na tabela DimCustomer e utilize o CASE para criar uma 4ª coluna com a informação de 'Masculino' ou 'Feminino'.

```sql
SELECT
  CostumerKey AS 'ID Cliente',
  FirstName AS 'Nome',
  Gender AS 'Sexo',
  CASE
    WHEN Gender = 'M' THEN 'Masculino'
    ELSE 'Feminino'
  END AS 'Sexo (CASE)'
FROM
  DimCustumer
```

## Aula 4: CASE WHEN WHEN... ELSE (Explicação)
- Crie um código para verificar a nota do aluno e determinar a situação:
  - Aprovado: nota maior ou igual a 6
  - Prova final: noa entre 4 e 6
  - Reprovado: nota abaixo de 4

```sql
DECLARE @varNota FLOAT
SET @varNota = 1

SELECT
  CASE
    WHEN @varNota >= 6 THEN 'Aprovado'
    WHEN @varNota >= 4 'Prova final'
    ELSE 'Reprovado'
  END
```

- Exemplo 2: Classifique o produto de acordo com o seu preço:
  - Preço >= 40000: Luxo
  - Preço >= 10000 e Preço < 40000: Econômico
  - Preço < 10000: Básico
 
```sql
DECLARE @varPreco FLOAT
SET @varPreco = 30000

SELECT
	CASE
		WHEN @varPreco >= 40000 THEN 'Luxo'
		WHEN @varPreco >= 10000 THEN 'Econômico'
		ELSE 'Básico'
	END
```

## Aula 5: CASE WHEN WHEN... ELSE (Exemplo)
- Crie uma coluna para substituir o 'M' por 'Masculino' e 'F' por 'Feminino'. Verifique se será necessário fazer alguma correção.

```sql
SELECT
  CustomerKey,
  FirstName,
  Gender
  CASE
    WHEN Gender = 'M' THEN 'Masculino'
    WHEN Gender = 'F' THEN 'Feminino'
    ELSE 'Empresa'
  END AS 'Sexo'
FROM
  DimCustomer
```

## Aula 6: CASE com os operadores lógicos AND e OR
- Faça uma consulta à tabela DimProduct e retorne as colunas ProductName, BrandName, ColorName, UnitPrice e uma coluna de preço com desconto.
- a) Caso o produto seja da marca Contoso E da cor Red, o desconto do produto será de 10%. Caso contrário, não terá nenhum desconto.

```sql
SELECT
  ProductName,
  BrandName,
  Colorname,
  UnitPrice
  CASE
    WHEN BrandName = 'Contoso' AND ColorName = 'Red' THEN 0.1
    ELSE 0
  END AS 'Preço com desconto'
FROM
  DimProduct
```

- b) Caso o produto seja da marca Litware OU Fabrikam, ele receberá um desconto de 5%. Caso contrário, não terá nenhum desconto.

```sql
SELECT
  ProductName,
  BrandName,
  Colorname,
  UnitPrice
  CASE
    WHEN BrandName = 'Litware' OR BrandName = 'Fabrikam' THEN 0.05
    ELSE 0
  END AS 'Preço com desconto'
FROM
  DimProduct  
```
## Aula 7: CASE Aninhado
- 4 Cargos (Title):
  - Sales Group Manager
  - Sales Region Manager
  - Sales State Manager
  - Sales Store Manager

  - Assalariado (SalariedFlag)?
  - SalariedFlag = 0: não é assalariado
  - SalariedFlag = 1: é assalariado

  - Situação: Cálculo do bônus
  - Sales Group Manager: Se for assalariado, 30%; Se não, 20%
  - Sales Region Manager: 15%
  - Sales State Manager: 7%
  - Sales Store Manager: 2%

```sql
SELECT
  FirstName,
  Title,
  SalariedFlag,
  CASE
    WHEN Title = 'Sales Group Manager' THEN
      CASE
        WHEN SalariedFlag = 1 THEN 0.3
        ELSE 0.2
      END
    WHEN Title = 'Sales Region Manager' THEN 0.15
    WHEN Title = 'Sales State Manager' THEN 0.07
    ELSE 0.02
  END AS 'Bônus'
FROM
  DimEmployee
```

## Aula 8: CASE Aditivo
- Os produtos da categoria 'TV and Video' terão um desconto de 10%. Se além de ser da categoria 'TV and Video', o produto for da subcategoria 'Televisions', receberá mais 5%. Total, 15%.

```sql
SELECT
  ProductKey,
  ProductName,
  ProductCategoryName,
  ProductSubcategoryName,
  UnitPrice,
  CASE WHEN ProductCategoryName = 'TV and Video'
    THEN 0.1 ELSE 0 END
  + CASE WHEN ProductSubcategoryName = 'Televisions'
    THEN 0.15 END
FROM DimProduct
INNER JOIN DimProductSubcategory
  ON DimProduct.ProductSubcategoryKey = DimProductSubcategory.ProductSubcategoryKey
    INNER JOIN DimproductCategory
      ON DimproductSubcategory.ProductCategoryKey = DimProductCategory.ProductCategoryKey
```

## Aula 9: IIF (Alternativa ao CASE)
- Qual é a categoria de risco do projeto abaixo, de acordo com a sua nota:
  - Risco Alto: Classicacao >= 5
  - Risco Baixo: Classificacao < 5

```sql
DECLARE @varClassificacao INT
SET @varClassificacao = 9

SELECT
  IIF(
    @varClassificacao >= 5,
    'Risco Alto',
    'Risco Baixo'
  )
```
	
- Crie uma coluna única de 'Cliente', contendo o nome do cliente, seja ele uma pessoa ou uma empresa. Traga também a coluna de CustomerKey e CustomerType.

```sql
SELECT
  CustomerKey,
  CustomerType,
  IIF(
    CustomerType = 'Person',
    FirstName,
    Company
  ) AS 'Cliente'
FROM
  DimCustomer
```

## Aula 10: IIF Composto
- Existem 3 tipos de estoque: High, Mid e Low. Faça um SELECT contendo as colunas de ProductKey, ProductName, StockTypeName e Nome do responsável pelo produto, de acordo com o tipo de estoque. A regra deverá ser a seguinte:
  - João é responsável pelos produtos High
  - Maria é responsável pelos produtos Mid
  - Luis é responsável pelos produtos Low

```sql
SELECT
  ProductKey,
  ProductName,
  StockTypeName,
  IFF(
    StockTypeName = 'High',
    'João',
    IIF(
      StockTypeName = 'Mid',
      'Maria',
      'Luis'
    )
  ) AS 'Responsável'
FROM
  DimProduct
```

## Aula 11 de 18: ISNULL - Tratando valores nulos
- Faça uma consulta que substitua todos os valores nulos de CityName da tabela DimGeography pelo texto 'Local desconhecido'.

```sql
SELECT
  GeographyKey,
  ContinentName,
  CityName,
  ISNULL(CityName, 'Local desconhecido')
FROM
  DimGeography
```

## Aula 13: Exercício 1
- O setor de vendas decidiu aplicar um desconto aos produtos de acordo com a sua classe. O percentual aplicado deverá ser de:
	- Economy -> 5%
	- Regular -> 7%
	- Deluxe -> 9%

a) Faça uma consulta à tabela DimProduct que retorne as seguintes colunas: ProductKey, ProductName, e outras duas colunas que deverão retornar o % de Desconto e UnitPrice com desconto.
```sql
SELECT
	ProductKey AS 'ID Produto',
	ProductName AS 'Nome Produto',
	ClassName AS 'Classe',
	UniPrice AS 'Preço',
	CASE
		WHEN ClassName = 'Economy' THEN 0.05
		WHEN ClassName = 'Regular' THEN 0.07
		ELSE 0.09
	END AS '% Desconto',
	CASE
		WHEN ClassName = 'Economy' THEN (1-0.05)*UnitPrice
		WHEN ClassName = 'Regular' THEN (1-0.07)*UnitPrice
		ELSE (1-0.09)*UnitPrice
	END AS 'Preço com desconto'
FROM
	DimProduct
```

b) Faça uma adaptação no código para que os % de desconto de 5%, 7% e 9% sejam facilmente modificados (dica: utilize variáveis).

```sql
DECLARE @varDesEconomy FLOAT, DECLARE @varDesRegular FLOAT, DECLARE @varDesDeluxe FLOAT

SET @varDesEconomy = 0.05
SET @varDesRegular = 0.07
SET @varDesDeluxe = 0.09

SELECT
	ProductKey AS 'ID Produto',
	ProductName AS 'Nome Produto',
	ClassName AS 'Classe',
	UniPrice AS 'Preço',
	CASE
		WHEN ClassName = 'Economy' THEN @varDesEconomy
		WHEN ClassName = 'Regular' THEN @varDesRegular
		ELSE @varDesDeluxe
	END AS '% Desconto',
	CASE
		WHEN ClassName = 'Economy' THEN (1-@varDesEconomy)*UnitPrice
		WHEN ClassName = 'Regular' THEN (1-@varDesRegular)*UnitPrice
		ELSE (1-@varDesDeluxe)*UnitPrice
	END AS 'Preço com desconto'
FROM
	DimProduct
```

## Aula 14: Exercício 2
- Você ficou responsável pelo controle de produtos da empresa e deverá fazer uma análise da quantidade de produtos por Marca. A divisão das marcas em categorias deverá ser a seguinte:
	- CATEGORIA A: Mais de 500 produtos
	- CATEGORIA B: Entre 100 e 500 produtos
	- CATEGORIA C: Menos de 100 produtos

Faça uma consulta à tabela DimProduct e retorne uma tabela com um agrupamento de Total de Produtos por Marca, além da coluna de Categoria, conforme a regra acima.

```sql
SELECT
	BrandName AS 'Marca',
	COUNT(*) AS 'Qtd. Produtos',
	CASE
		WHEN COUNT(*) >= 500 THEN 'Categoria A'
		WHEN COUNT(*) >= 100 THEN 'Categoria B'
		ELSE 'Categoria C'
	END AS 'Categoria'
FROM
	DimProduct
GROUP BY BrandName
```

## Aula 15: Exercício 3
- 3. Será necessário criar uma categorização de cada loja da empresa considerando a quantidade de funcionários de cada uma. A lógica a ser seguida será a lógica abaixo:
	- EmployeeCount >= 50; 'Acima de 50 funcionários'
	- EmployeeCount >= 40; 'Entre 40 e 50 funcionários'
	- EmployeeCount >= 30; 'Entre 30 e 40 funcionários'
	- EmployeeCount >= 20; 'Entre 20 e 30 funcionários'
	- EmployeeCount >= 40; 'Entre 10 e 20 funcionários'
	- Caso contrário: 'Abaixo de 10 funcionários'

Faça uma consulta à tabela DimStore que retorne as seguintes informações: StoreName, EmployeeCount e a coluna de categoria, seguindo a regra acima.

```sql
SELECT
	StoreName AS 'Nome da Loja',
	EmployeeCount 'Qtd. funcionários',
	CASE
		WHEN EmployeeCount >= 50 THEN 'Acima de 50 funcionários'
		WHEN EmployeeCount >= 40 THEN 'Entre 40 e 50 funcionários'
		WHEN EmployeeCount >= 30 THEN 'Entre 30 e 40 funcionários'
		WHEN EmployeeCount >= 20 THEN 'Entre 20 e 30 funcionários'
		WHEN EmployeeCount >= 10 THEN 'Entre 10 e 20 funcionários'
		ELSE 'Abaixo de 10 funcionários'
	END AS 'Categoria'
FROM
	DimStore
```

## Aula 16: Exercício 4
- O setor de logística deverá realizar um transporte de carga dos produtos que estão no depósito de Seattle para o depósito de Sunnyside. Não se tem muitas informações sobre os produtos que estão no depósito, apenas se sabe que existem 100 exemplares de cada Subcategoria. Ou seja, 100 laptops, 100 câmeras digitais, 100 ventiladores, e assim vai. O gerente de logística definiu que os produtos serão transportados por duas rotas distintas. Além disso, a divisão dos produtos em cada uma das rotas será feita de acordo com as subcategorias (ou seja, todos os produtos de uma mesma subcategoria serão transportados pela mesma rota):

	- Rota 1: As subcategorias que tiverem uma soma total menor que 1000 kg deverão ser transportados pela Rota 1.
	- Rota 2: As subcategorias que tiverem uma soma total maior ou igual a 1000 kg deverão ser transportados pela Rota 2.

Você deverá realizar uma consulta à tabela DimProduct e fazer essa divisão das subcategorias por cada rota. Algumas dicas:
	- Dica 1: A sua consulta deverá ter um total de 3 colunas: Nome da Subcategoria, Peso Total e Rota.
	- Dica 2: Como não se sabe quais produtos existem no depósito, apenas que existem 100 exemplares de cada subcategoria, você deverá descobrir o peso médio de cada subcategoria e multiplicar essa média por 100, de forma que você descubra aproximadamente qual é o peso total dos produtos por subcategoria.
	- Dica 3: Sua resposta final deverá ter um JOIN e um GROUP BY.

```sql
SELECT
	ProductSubcategoryName AS 'Nome da Subcategoria',
	ROUND(AVG(Weight)*100, 2) AS 'Peso Total',
	CASE
		WHEN ROUND(AVG(Weight)*100, 2) < 1000 THEN 'Rota 1'
		ELSE 'Rota 2'
	END AS 'Rota'
FROM
	DimProduct
INNER JOIN DimProductSucategory
	ON DimProduct.ProductSubcategoryKey = DimProductSucategory.ProductSubcategoryKey
GROUP BY ProductSubcategoryName
```

## Aula 17: Exercício 5
- O setor de marketing está com algumas ideias de ações para alavancar as vendas em 2021. Uma delas consiste em realizar sorteios entre os clientes da empresa. Este sorteio será dividido em categorias:
	- ‘Sorteio Mãe do Ano’: Nessa categoria vão participar todas as mulheres com filhos.
	- ‘Sorteio Pai do Ano’: Nessa categoria vão participar todos os pais com filhos.
	- ‘Caminhão de Prêmios’: Nessa categoria vão participar todas os demais clientes (homens e mulheres sem filhos).

Seu papel será realizar uma consulta à tabela DimCustomer e retornar 5 colunas:
	- FirstName AS ‘Nome’
	- Gender AS ‘Sexo’
	- TotalChildren AS ‘Qtd. Filhos’
	- EmailAdress AS ‘E-mail’
	- Ação de Marketing: nessa coluna você deverá dividir os clientes de acordo com as categorias ‘Sorteio Mãe do Ano’, ‘Sorteio Pai do Ano’ e ‘Caminhão de Prêmios’.

```sql
SELECT
	FirstName AS 'Nome',
	Gender AS 'Sexo',
	TotalChildren AS 'Qtd. Filhos',
	EmailAdress AS 'E-mail',
	CASE
		WHEN Gender = 'F' AND TotalChildren > 0 THEN ‘Sorteio Mãe do Ano’
		WHEN Gender = 'M' and TotalChildren > 0 THEN ‘Sorteio Pai do Ano’
		ELSE ‘Caminhão de Prêmios’
	END AS 'Ação de Marketing'
FROM
	DimCustomer
```

## Aula 18: Exercício 6
- Descubra qual é a loja que possui o maior tempo de atividade (em dias). Você deverá fazer essa consulta na tabela DimStore, e considerar a coluna OpenDate como referência para esse cálculo.
Atenção: lembre-se que existem lojas que foram fechadas.

```sql
SELECT
	StoreName,
	OpenDate,
	CloseDate,
	CASE
		WHEN CloseDate IS NULL THEN DATEDIFF(DAY, OpenDate, GETDATE())
		ELSE DATEDIFF(DAY, OpenDate, CloseDate)
	END AS 'Dias de atividade'
FROM
	DimStore
```


------------
## Módulo 13: SQL Views

### Aula 2: CREATE VIEW - Criando a primeira View

```sql
-- 1. Exemplos
-- a) Crie uma view contendo as seguintes informações da tabela DimCustomer: FirstName, EmailAddress e BirthDate. Chame essa view de vwClientes

CREATE VIEW vwCliente AS
SELECT
	FirstName AS 'Nome',
	EmailAdress AS 'E-mail',
	BirthDate AS 'Data de Nascimento'
FROM
	DimCustomer

-- b) Crie uma View contendo as seguintes informações da tabela DimProduct: ProductKey, ProductName, BrandName e UnitPrice. Chame essa view de vwProdutos

CREATE VIEW vwProdutos AS
SELECT
	ProductKey AS 'ID Produto',
	ProductName As 'Nome do Produto',
	ProductSubcategoryKey AS 'ID Subcategoria',
	BrandName As 'Marca'
	UnitPrice As 'Preço Unitário'
FROM
	DimProduct
```


### Aula 3: Como assim 'the only statement in the batch'
- Utilizando o GO para delimitar as views.

```sql
-- VIEW 1
CREATE VIEW vwCliente AS
SELECT
	FirstName AS 'Nome',
	EmailAdress AS 'E-mail',
	BirthDate AS 'Data de Nascimento'
FROM
	DimCustomer
GO

-- VIEW 2

GO
CREATE VIEW vwProdutos AS
SELECT
	ProductKey AS 'ID Produto',
	ProductName As 'Nome do Produto',
	ProductSubcategoryKey AS 'ID Subcategoria',
	BrandName As 'Marca'
	UnitPrice As 'Preço Unitário'
FROM
	DimProduct
GO
```


### Aula 4: USE Database - Como especificar o banco de dados com USE

```sql
USE Teste
SELECT * FROM Produtos

USE ContosoRetailDW
SELECT * FROM DimProduct
```


### Aula 5: ALTER VIEW
- Altere a view abaixo para incluir apenas os clientes do sexto Feminino

```sql
GO
ALTER VIEW vwClientes AS
SELECT
	FirstName As 'Nome',
	EmailAdress AS 'E-mail',
	BirthDate AS 'Data de Nascimento',
	Gender AS 'Sexo'
FROM
	DimCustomer
WHERE Gender = 'F'
GO
```


### Aula 6 de 13: DROP VIEW
- Exemplo: Exclua as views vwClientes e vwProdutos

```sql
DROP VIEW vwClientes
DROP VIEW vwProdutos
```


### Aula 8: Resolução Exercício 1
- a) A partir da tabela DimProduct, crie uma View contendo as informações de ProductName, ColorName, UnitPrice e UnitCost, da tabela DimProduct. Chame essa View de vwProdutos.

```sql
CREATE VIEW vwProdutos AS
SELECT
	ProductName AS 'Nome',
	ColorName As 'Cor',
	UnitPrice AS 'Preço',
	UnitCost As 'Custo'
FROM
	DimProduct
GO
```

- b) A partir da tabela DimEmployee, crie uma View mostrando FirstName, BirthDate, DepartmentName. Chame essa View de vwFuncionarios.

```sql
GO
CREATE VIEW vwFuncionarios AS
SELECT
	FirstName AS 'Nome',
	BirthDate AS 'Data de nascimento',
	DepartmentName As 'Departamento'
FROM
	DimEmployee
GO
```

- c) A partir da tabela DimStore, crie uma View mostrando StoreKey, StoreName e OpenDate. Chame essa View de vwLojas.

```sql
GO
CREATE VIEW vwLojas AS
SELECT
	StoreKey AS 'ID Loja',
	StoreName AS 'Nome da loja',
	OpenDate AS 'Data de abertura'
FROM
	DimStore
GO
```



### Aula 9: Resolução Exercício 2
- Crie uma View contendo as informações de Nome Completo (FirstName + LastName), Gênero (por extenso), E-mail e Renda Anual (formatada com R$). Utilize a tabela DimCustomer. Chame essa View de vwClientes.

```sql
GO
CREATE VIEW vwClientes AS
SELECT
	CONCAT(FirstName, ' ', LastName) AS 'Nome Completo',
	REPLACE(REPLACE(Gender, 'M', 'Masculino'), 'F', 'Feminino') AS 'Gênero',
	EmailAdress AS 'E-mail',
	FORMAT(YearlyIncome, 'c') AS 'Renda Anual'
FROM
	DimCustomer
GO
```


### Aula 10: Resolução Exercício 3
- a) A partir da tabela DimStore, crie uma View que considera apenas as lojas ativas. Faça um SELECT de todas as colunas. Chame essa View de vwLojasAtivas.

```sql
GO
CREATE VIEW vwLojasAtivas AS
SELECT * FROM DimStore
WHERE Status = 'On'
GO
```

- b) A partir da tabela DimEmployee, crie uma View de uma tabela que considera apenas os funcionários da área de Marketing. Faça um SELECT das colunas: FirstName, EmailAddress e DepartmentName. Chame essa de vwFuncionariosMkt.

```sql
GO
CREATE VIEW vwFuncionariosMkt AS
SELECT
	FirstName,
	EmailAdress,
	DepartmentName
FROM
	DimEmployee
WHERE DepartmentName = 'Marketing'
GO
```

- c) Crie uma View de uma tabela que considera apenas os produtos das marcas Contoso e Litware. Além disso, a sua View deve considerar apenas os produtos de cor Silver. Faça um SELECT de todas as colunas da tabela DimProduct. Chame essa View de vwContosoLitwareSilver.

```sql
GO
CREATE VIEW vwContosoLitwareSilver AS
SELECT * FROM DimProduct
WHERE BrandName IN ('Contoso', 'Litware') AND ColorName = 'Silver'
GO
```


### Aula 11: Resolução Exercício 4
- Crie uma View que seja o resultado de um agrupamento da tabela FactSales. Este agrupamento deve considerar o SalesQuantity (Quantidade Total Vendida) por Nome do Produto. Chame esta View de vwTotalVendidoProdutos. OBS: Para isso, você terá que utilizar um JOIN para relacionar as tabelas FactSales e DimProduct.

```sql
GO
CREATE VIEW vwTotalVendidoProdutos AS
SELECT
	ProductName AS 'Nome do produto',
	SUM(SalesQuantity) AS 'Qtd. Vendida'
FROM
	FactSales
INNER JOIN DimProduct
	ON FactsSales.ProductKey = DimProduct.ProductKey
GROUP BY ProductName
GO
```


### Aula 12: Resolução Exercício 5
- Faça as seguintes alterações nas tabelas da questão 1.
- a) Na View criada na letra a da questão 1, adicione a coluna de BrandName.

```sql
GO
ALTER VIEW vwProdutos AS
SELECT
	ProductName AS 'Nome',
	ColorName As 'Cor',
	UnitPrice AS 'Preço',
	UnitCost AS 'Custo',
	BrandName AS 'Marca'
FROM
	DimProduct
GO
```

- b) Na View criada na letra b da questão 1, faça um filtro e considere apenas os funcionários do sexo feminino.

```sql
GO
ALTER VIEW vwFuncionarios AS
SELECT
	FirstName AS 'Nome',
	BirthDate AS 'Data de nascimento',
	DepartmentName As 'Departamento'
FROM
	DimEmployee
WHERE Gender = 'F'
GO
```

- c) Na View criada na letra c da questão 1, faça uma alteração e filtre apenas as lojas ativas.

```sql
GO
ALTER VIEW vwLojas AS
SELECT
	StoreKey AS 'ID Loja',
	StoreName AS 'Nome da loja',
	OpenDate AS 'Data de abertura'
FROM
	DimStore
WHERE Status = 'On'
GO
```


### Aula 16: Resolução Exercício 6
- a) Crie uma View que seja o resultado de um agrupamento da tabela DimProduct. O resultado esperado da consulta deverá ser o total de produtos por marca. Chame essa View de vw_6a.

```sql
GO
CREATE VIEW vw_6a
SELECT
	BrandName AS 'Marca',
	COUNT(*) AS 'Qtd. Produtos'
FROM
	DimProduct
GROUP BY BrandName
GO
```

- b) Altere a View criada no exercício anterior, adicionando o peso total por marca. Atenção: sua View final deverá ter então 3 colunas: Nome da Marca, Total de Produtos e Peso Total.

```sql
GO
ALTER VIEW vw_6a
SELECT
	BrandName AS 'Marca',
	COUNT(*) AS 'Qtd. Produtos',
	SUM(Weight) AS 'Peso Total'
FROM
	DimProduct
GROUP BY BrandName
GO
```

- c) Exclua a View vw_6a.

```sql
DROP VIEW vw_6a
```


--------------
## Módulo 14: CRUD

### Aula 3: CREATE e DROP DATABASE

```sql
CREATE DATABASE Teste
DROP DATABASE Teste
CREATE BDImpressionador
```

### Aula 5: Aula 5 de 21: Cuidados antes de criar uma Tabela em um Banco de Dados

```sql
USE BDImpressionador
```

### Aula 6: CREATE TABLE - Criando a primeira tabela
- Crie uma tabela chamada 'Produtos'. Essa abela deve conter 4 colunas: id_produt, nome_produto, data_validade e preco_produto. Certifique-se de que o tipo das colunas está correto.

```sql
USE BDImpressionador

CREATE TABLE Produtos(
	id_produto INT,
	nome_produto VARCHAR(200),
	data_validade DATETIME,
	preco_produto FLOAT
)
```


### Aula 7: INSERT SELECT - Adicionando dados de outra tabela
- Adicionando valores de outra tabela

```sql
INSERT INTO Produtos(id_produto, nome_produto, data_validade, preco_produto)
SELECT
	ProductKey,
	ProductName,
	AvailableForSaleDate,
	UnitPrice
FROM
	ContosoRetailDW.dbo.DimProduct
```


### Aula 8: INSERT INTO - Adicionando novos valores na tabela
- Adicionando novos valores na tabela

```sql
INSERT INTO Produtos(id_produto, nome_produto, data_validade, preco_produto)
VALUES
	(1, 'Arroz', '31/12/2021', 22.50)
	(2, 'Feijão', '20/11/2022', 8.99)
```


### Aula 10: UPDATE - Atualizando o dado de uma tabela
- Atualizando o dado de uma tabela

```sql
UPDATE Produtos
SET nome_produto = 'Macarrão'
WHERE id_produto = 2
```


### Aula 11: DELETE - Deletando dados
- Deletando dados de uma tabela

```sql
DELETE
FROM Produtos
WHERE id_produto = 3
```


### Aula 12: DROP TABLE - Excluindo uma tabela
- Excluindo uma tabela

```sql
DROP TABLE Produtos
```


### Aula 13: Código da tabela utilizada nos próximos exemplos

```sql
USE BDImpressionador

CREATE TABLE Funcionarios(
	id_funcionario int,
	nome_funcionario varchar(100),
	salario float,
	data_nascimento date
)

INSERT INTO Funcionarios(id_funcionario, nome_funcionario, salario, data_nascimento)
VALUES
	(1, 'Lucas'		, 1500, '20/03/1990'),
	(2, 'Andressa'	, 2300, '07/12/1988'),
	(3, 'Felipe'	, 4000, '13/02/1993'),
	(4, 'Marcelo'	, 7100, '10/04/1993'),
	(5, 'Carla'		, 3200, '02/09/1986'),
	(6, 'Juliana'	, 5500, '21/01/1989'),
	(7, 'Mateus'	, 1900, '02/11/1993'),
	(8, 'Sandra'	, 3900, '09/05/1990'),
	(9, 'André'		, 1000, '13/03/1994'),
	(10, 'Julio'	, 4700, '05/07/1992')

```


### Aula 14: ALTER TABLE
- ALTER TABLE: Adicionando, deletar ou modificar tipo de dados de uma coluna
- Adicionar coluna:

```sql
ALTER TABLE Funcionarios
ADD cargo VACHAR(100), bonus FLOAT
```

- Atualizando valores:

```sql
UPDATE Funcionarios
SET cargo = 'Analista', bonus = 0.15
WHERE id_funcionario = 1
```

- Alterar tipo de dados de uma coluna:

```sql
ALTER TABLE Funcionarios
ALTER COLUMN salario INT
```

- Deletar coluna:

```sql
ALTER TABLE Funcionarios
DROP COLUMN cargo, bonus
```

### Aula 16: Resolução Exercício 1
- a) Crie um banco de dados chamado BD_Teste.

```sql
CREATE DATABASE BD_Teste
```

- b) Exclua o banco de dados criado no item anterior.

```sql
DROP DATABASE BD_Teste
```

- c) Crie um banco de dados chamado Exercicios.

```sql
CREATE DATABASE Exercicios
```


### Aula 17: Resolução Exercício 2
- No banco de dados criado no exercício anterior, crie 3 tabelas, cada uma contendo as seguintes colunas. Lembre-se dos seguintes pontos: a) Garantir que o Banco de Dados Exercicios está selecionado. b) Definir qual será o tipo de dados mais adequado para cada coluna das tabelas. Lembrando que os tipos de dados mais comuns são: INT, FLOAT, VARCHAR e DATETIME. Por fim, faça um SELECT para visualizar cada tabela.

- Tabela 1: dCliente (ID_Cliente, Nome_Cliente, Data_de _Nascimento)

```sql
USE Exercicios

CREATE TABLE dCliente(
	ID_Cliente INT,
	Nome_Cliente VARCHAR(100),
	Data_de_Nascimento DATETIME
)

SELECT * from dClientes
```

- Tabela 2: dGerente (ID_Gerente, Nome_Gerente, Data_de_Contratacao, Salario)

```sql
USE Exercicios

CREATE TABLE dGerente(
	ID_Gerente INT,
	Nome_Gerente VARCHAR(200),
	Data_de_Contratacao DATETIME,
	Salario FLOAT
)

SELECT * FROM dGerente
```
 
- Tabela 3: fContratos (ID_Contrato, Data_de_Assinatura, ID_Cliente, ID_Gerente, Valor_do_Contrato)

 ```sql
USE Exercicios

CREATE TABLE dContratos(
	ID_Contrato INT,
	Data_de_Assinatura DATETIME,
	ID_Cliente, INT
	ID_Gerente INT,
	Valor_do_Contrato FLOAT
)

SELECT * FROM dContratos
```


### Aula 18: Resolução Exercício 3
- Em cada uma das 3 tabelas, adicione os seguintes valores:
- Tablea dCliente
![image](https://github.com/user-attachments/assets/cdc55860-c881-4018-b56f-4e616b35a42b)

```sql
USE Exercicios

INSER INTO dCliente(ID_Cliente, Nome_Cliente, Data_de_Nascimento)
VALUES
	(1, 'André Martins', '1989-02-12'),
	(2, 'Bárbara Campos', '1992-05-07'),
	(3, 'Carol Freitas', '1985-04-23'),
	(4, 'Diego Cardoso', '1994-10-11'),
	(5, 'Eduardo Pereira', '1988-11-09'),
	(6, 'Fabiana Silva', '1989-09-02'),
	(7, 'Gustavo Barbosa', '1993-06-17'),
	(8, 'Helen Viana', '1990-02-11')
```

- Tabela dGerente
![image](https://github.com/user-attachments/assets/7846c717-614e-4774-8a15-2648ca646dc2)

```sql
USE Exercicios

INSERT INTO dGerente(ID_Gerente, Nome_Gerente, Data_de_Contratacao, Salario)
VALUES
	(1, 'Lucas Sampaio', '2015-03-21', 6700),
	(2, 'Mariana Padilha', '2011-01-10', 9900),
	(3, 'Nathália Santos', '2018-10-03', 7200),
	(4, 'Otávio Costa', '2017-04-18', 11000)
```

- Tabela fContratos
![image](https://github.com/user-attachments/assets/0f68015e-d44e-4126-9b16-3d05edbbc4dd)

```sql
USE Exercicios

INSERT INTO fContratos(ID_Contrato, Data_de_Assinatura, ID_Cliente, ID_Gerente, Valor_do_Contrato)
VALUES
	(1, '2019-01-12', 8, 1, 23000),
	(2, '2019-02-10', 3, 2, 15500),
	(3, '2019-03-07', 7, 2, 6500),
	(4, '2019-03-15', 1, 3, 33000),
	(5, '2019-03-21', 5, 4, 11100),
	(6, '2019-03-23', 4, 2, 5500),
	(7, '2019-03-28', 9, 3, 55000),
	(8, '2019-04-04', 2, 1, 31000),
	(9, '2019-04-05', 10, 4, 3400),
	(10, '2019-04-05', 6, 2, 9200)
```

### Aula 19: Resolução Exercício 4
- Novos dados deverão ser adicionados nas tabelas dCliente, dGerente e fContratos. Fique livre para adicionar uma nova linha em cada tabela contendo, respectivamente.
- (1) um novo cliente (id cliente, nome e data de nascimento)

```sql
INSER INTO dCliente(ID_Cliente, Nome_Cliente, Data_de_Nascimento)
VALUES
	(9, 'Mikelly Lima', '1995-12-03')
```

- (2) um novo gerente (id gerente, nome, data de contratação e salário)

```sql
INSERT INTO dGerente(ID_Gerente, Nome_Gerente, Data_de_Contratacao, Salario)
VALUES
	(5, 'Mikelly Lima', '2025-12-07', 15000)
```

(3) um novo contrato (id, data assinatura, id cliente, id gerente, valor do contrato)

```sql
INSERT INTO fContratos(ID_Contrato, Data_de_Assinatura, ID_Cliente, ID_Gerente, Valor_do_Contrato)
VALUES
	(11, '2025-10-12', 9, 5, 100000)
```


### Aula 20: Resolução Exercício 5
- O contrato de ID igual a 4 foi registrado com alguns erros na tabela fContratos. Faça uma alteração na tabela atualizando os seguintes valores:
	- Data_de_Assinatura: 17/03/2019
	- ID_Gerente: 2
	- Valor_do_Contrato: 33500

```sql
USE Exercicios

UPDATE fContratos
SET Data_de_Assinatura = '2019-03-17',
	ID_Gerente = 2,
	Valor_do_Contrato = 33500
WHERE ID_Contrato = 4
```

### Aula 21: Resolução Exercício 6
- Delete a linha da tabela fContratos que você criou na questão 4.

```sql
USE Exercicios

DELETE
FROM fContratos
WHERE ID_Contrato = 11
```


------------
## Módulo 15: 

### Aula 3: Subquery na prática - Aplicação com o Where (Exemplo 1)
- Exemplo 1: Quais produtos da tabela DimProduct possuem custos acima da média?

```sql
SELECT
	*
FROM
	DimProduct
WHERE UnitCost > (SELECT AVG(UnitCost) FROM DimProduct)
```


### Aula 4: Subquery na prática - Aplicação com o Where (Exemplo 2)
- - Exemplo 2: Faça uma consulta para retornar os produtos da categoria 'Televisions'. Tome cuidado pois não temos a informação de Nome da Subcategoria na tabela DimProduct. Dessa forma, precisaremos criar um SELECT que descubra o ID da categoria 'Televisions' e passar esse resultado como o valor que queremos filtrar dentro do WHERE.

```sql
SELECT
	*
FROM
	DimProduct
WHERE ProductSubcategoryKey =
	(SELECT ProductSubcategoryKey FROM DimProductSubcategory
		WHERE ProductSubcategoryName = 'Televisions')
```


### Aula 5: Subquery na prática - Aplicação com o Where (Exemplo 3)
- Exemplo 3: Filtre a tabela FactSales e mostre apenas as vendas referentes às lojas com 100 ou mais funcionários

```sql
SELECT * FROM FactSales
WHERE StoreKey IN (
	SELECT
		StoreKey
	FROM
		DimStore
	WHERE EmployeeCount >= 100)
```


### Aula 6 de 28: ANY, SOME e ALL

```sql
CREATE TABLE funcionarios(
id_funcionario INT,
nome VARCHAR(50),
idade INT,
sexo VARCHAR(50))

INSERT INTO funcionarios(id_funcionario, nome, idade, sexo)
VALUES	
	(1, 'Julia', 20, 'F'),
	(2, 'Daniel', 21, 'M'),
	(3, 'Amanda', 22, 'F'),
	(4, 'Pedro', 23, 'M'),
	(5, 'André', 24, 'M'),
	(6, 'Luisa', 25, 'F')
```

- Selecione os funcionários do sexo masculino (MAS, utilizando a coluna de IDADE para isso)

```sql
SELECT * FROM funcionarios
WHERE Idade IN (21, 23, 24)

SELECT * FROM funcionarios
WHERE Idade IN (SELECT Idade FROM funcionarios WHERE sexo = 'M')

/*
= ANY(valor1, valor2, valor3) :
Equivalente ao IN, retorna as lunhas da tabela que sejam iguais ao valor1, OU valor2, OU valor3
*/

SELECT * FROM funcionarios
WHERE Idade = ANY (SELECT Idade FROM funcionarios WHERE sexo = 'M')

/*
> ANY(valor1, valor2, valor3) :
Retorna as linhas da tabela com valores maiores que o valor1, OU valor2, OU valor3. Ou seja, maior que o mínimo dos valores
*/

SELECT * FROM funcionarios
WHERE Idade > ANY (SELECT Idade FROM funcionarios WHERE sexo = 'M')

/*
< ANY(valor1, valor2, valor3) :
Retorna as linhas da tabela com valores maiores que o valor1, OU valor2, OU valor3. Ou seja, maior que o máximo dos valores
*/

SELECT * FROM funcionarios
WHERE Idade < ANY (SELECT Idade FROM funcionarios WHERE sexo = 'M')

-- O ANY pode ser substituído pelo SOME.

/*
> ALL(valor1, valor2, valor3) :
Retorna as linhas da tabela com valores maiores que o valor1, E valor2, E valor3. Ou seja, maior que o máximo dos valores
*/

SELECT * FROM funcionarios
WHERE Idade > ALL (SELECT Idade FROM funcionarios WHERE sexo = 'M')

/*
< ALL(valor1, valor2, valor3) :
Retorna as linhas da tabela com valores menores que o valor1, E valor2, E valor3. Ou seja, menor que o mínimo dos valores
*/

SELECT * FROM funcionarios
WHERE Idade < ALL (SELECT Idade FROM funcionarios WHERE sexo = 'M')
```


### Aulas 7: EXISTS
- Exemplo: Retornar uma tabela com todos os produtos (ID Produto e Nome Produto) que possuem alguma venda no dia 01/01/2007

```sql
SELECT
	Productkey,
	ProductName
FROM
	DimProduct
WHERE EXISTS(
	SELECT
		ProductKey
	FROM
		FactSales
	WHERE
		Datekey = '01/01/2007'
		AND FactSales.ProductKey = DimProduct.ProductKey
	)
```


### Aula 9: Subquery na prática - Aplicação com o SELECT
- Exemplo: Retornar uma tabela com todos os produtos (ID Produto e Nome Produto) e também o total de vendas para cada produto

```sql
SELECT
	ProductKey,
	ProductName,
	(SELECT COUNT(ProductKey) FROM FactSales WHERE FactSales.ProductKey = DimProduct.ProductKey) AS 'Qtd. Vendas'
FROM
	DimProduct
```


### Aula 10: Subquery na prática - Aplicação com o FROM
- Exemplo: Retornar a quantidade total de produtos da marca Contoso.

```sql
-- Possibilidade 1
SELECT
	COUNT(*)
FROM DimProduct
WHERE BrandName = 'Contoso'

-- Possibilidade 2
SELECT
	COUNT(*)
FROM
	(SELECT * FROM DimProduct WHERE BrandName = 'Contoso') AS T
```


### Aula 12: Subquery aninhada
- Exemplo: Descubra os nomes dos clientes que ganham o segundo maior salário.

```sql
SELECT
	*
FROM
	DimCustomer
WHERE CustomerType = 'Person'
ORDER BY YearlyIncome DESC


SELECT
	DISTINCT TOP(2) YearlyIncome
FROM
	DimCustomer
WHERE CustomerType = 'Person'
ORDER BY YearlyIncome DESC


-- Etapas
--1. Descobrir o maior salário
--2. Descobrir o segundo maior salário
--3. Descobrir os nomes dos clientes que ganham o segundo maior salário
```


### Aula 13: Subquery aninhada
- Exemplo: Descubra os nomes dos clientes que ganham o segundo maior salário.

```sql
-- Etapas
--1. Descobrir o maior salário
--2. Descobrir o segundo maior salário
--3. Descobrir os nomes dos clientes que ganham o segundo maior salário

SELECT
	CustomerKey,
	FirstName,
	Lastname,
	YearlyIncome
FROM
	DimCustomer
WHERE YearlyIncome = (
	SELECT
		MAX(YearlyIncome)
	FROM
		DimCustomer
	WHERE YearlyIncome < (
		SELECT
			MAX(YearlyIncome)
		FROM
			DimCustomer
		WHERE CustomerType = 'Person'
	)

)
```


### Aula 14: CTE - O que é e como criar
- Exemplo: Crie uma CTE para armazenar o resultado de uma consulta que contenha: ProductKey, ProductName, BrandName, ColorName e UnitPrice, apenas para a marca Contoso.

```sql
WITH cte AS (
SELECT
	ProductKey,
	ProductName,
	BrandeName,
	ColorName,
	UnitPrice
FROM
	DimProduct
WHERE BrandName = 'Contoso'
)
```


### Aula 15: Calculando agregações com CTE
- Exemplo: Crie uma CTE que seja o resultado do agrupamento de total de produtos por marca. Faça uma média de produtos por marca.

```sql
WITH cte AS (
SELECT
	BrandName,
	COUNT(*) AS 'Total'
FROM
	DimProduct
GROUP BY BrandName
)

SELECT AVG(Total) FROM cte
```


### Aula 16: Nomeando colunas de uma CTE
- Exemplo: Crie uma CTE que seja o resultado do agrupamento de total de produtos por marca. Faça uma média de produtos por marca.

```sql
WITH cte (Marca, Total) AS (
SELECT
	BrandName,
	COUNT(*)
FROM
	DimProduct
GROUP BY BrandName
)

SELECT AVG(Total) FROM cte 
```


### Aula 17: Criando múltiplas CTE's
- Exemplo: Crie 2 CTE's
- 1. A primeira, chamada produtos_contoso, deve conter as seguintes colunas (DimProduct): ProductKey, ProductName, BrandName
- 2. A segunda, chamada vendas_top100, deve ser um top 100 vendas mais recentes, considerando as seguintes colunas da tabela FactSales: SalesKey, ProductKey, DateKey, SalesQuantity
- Por fim, faça um INNER JOIN dessas tabelas

```sql
WITH produtos_contoso AS (
SELECT
	ProductKey,
	ProductName,
	BrandName
FROM
	DimProduct
WHERE BrandName = 'Contoso'
),
vendas_top100 (
SELECT TOP(100)
	SalesKey,
	ProductKey,
	DateKey,
	SalesQuantity
FROM
	FactSales
ORDER BY DateKey DESC
)

SELECT * FROM vendas_top100
INNER JOIN produtos_contoso
	ON vendas_top100.ProductKey = produtos_contoso.ProductKey
```


### Aula 19: Resolução Exercício 1
- Para fins fiscais, a contabilidade da empresa precisa de uma tabela contendo todas as vendas referentes à loja ‘Contoso Orlando Store’. Isso porque essa loja encontra-se em uma região onde a tributação foi modificada recente. Portanto, crie uma consulta ao Banco de Dados para obter uma tabela FactSales contendo todas as vendas desta loja.

```sql
SELECT * FROM FactSales
WHERE StoreKey = (
	SELECT StoreKey FROM DimStore
	WHERE StoreName = 'Contoso Orlando Store'
)
```


### Aula 20: Resolução Exercício 2
- O setor de controle de produtos quer fazer uma análise para descobrir quais são os produtos que possuem um UnitPrice maior que o UnitPrice do produto de ID igual a 1893.
- a) A sua consulta resultante deve conter as colunas ProductKey, ProductName e UnitPrice da tabela DimProduct.

```sql
SELECT
	ProductKey,
	ProductName,
	UnitPrice
FROM
	DimProduct
WHERE UnitPrice > (
	SELECT UnitPrice FROM DimProduct
	WHERE ProductKey = 1893
)
```

- b) Nessa query você também deve retornar uma coluna extra, que informe o UnitPrice do produto 1893.

```sql
SELECT
	ProductKey,
	ProductName,
	UnitPrice,
	(SELECT UnitPrice FROM DimProduct
	WHERE ProductKey = 1893) AS 'UnitPrice (ID 1983)'
FROM
	DimProduct
WHERE UnitPrice > (
	SELECT UnitPrice FROM DimProduct
	WHERE ProductKey = 1893
)
```


### Aula 21: Resolução Exercício 3
- A empresa Contoso criou um programa de bonificação chamado “Todos por 1”. Este programa consistia no seguinte: 1 funcionário seria escolhido ao final do ano como o funcionário destaque, só que a bonificação seria recebida por todos da área daquele funcionário em particular. O objetivo desse programa seria o de incentivar a colaboração coletiva entre os funcionários de uma mesma área. Desta forma, o funcionário destaque beneficiaria não só a si, mas também a todos os colegas de sua área.
Ao final do ano, o funcionário escolhido como destaque foi o Miguel Severino. Isso significa que todos os funcionários da área do Miguel seriam beneficiados com o programa. O seu objetivo é realizar uma consulta à tabela DimEmployee e retornar todos os funcionários da área “vencedora” para que o setor Financeiro possa realizar os pagamentos das bonificações.

```sql
SELECT * FROM DimEmployee
WHERE DepartmentName = (
	SELECT DepartmentName FROM DimEmployee
	WHERE FirstName = 'Miguel' AND LastName = 'Severino'
)
```


### Aula 22: Resolução Exercício 4
- Faça uma query que retorne os clientes que recebem um salário anual acima da média. A sua query deve retornar as colunas CustomerKey, FirstName, LastName, EmailAddress e YearlyIncome. Obs: considere apenas os clientes que são 'Pessoas Físicas'

```sql
SELECT
	CustomerKey,
	FirstName,
	LastName,
	EmailAdress,
	YearlyIncome
FROM
	DimCustomer
WHERE YearlyIncome > (
	SELECT AVG(YearlyIncome) FROM DimCustomer
	WHERE CustomerType = 'Person'
) AND CustomerType = 'Person'
```


### Aula 23: Resolução Exercício 5
-  A ação de desconto da Asian Holiday Promotion foi uma das mais bem sucedidas da empresa. Agora, a Contoso quer entender um pouco melhor sobre o perfil dos clientes que compraram produtos com essa promoção. Seu trabalho é criar uma query que retorne a lista de clientes que compraram nessa promoção.

```sql
-- 1) Descobrir o ID da promoção Asian Holiday Promotion
SELECT PromotionKey FROM DimPromotion
WHERE PromotionName = 'Asian Holiday Promotion'

-- 2) Descobrir os IDs dos clientes que compraram com essa promoção
SELECT
	CustomerKey
FROM FactOnlineSales
WHERE PromotionKey IN (
	SELECT PromotionKey FROM DimPromotion
	WHERE PromotionName = 'Asian Holiday Promotion'
)

-- 3) Descobrir as informações dos clientes
SELECT * FROM DimCustomer
WHERE CustomerKey IN (
	SELECT
		CustomerKey
	FROM FactOnlineSales
	WHERE PromotionKey IN (
		SELECT PromotionKey FROM DimPromotion
		WHERE PromotionName = 'Asian Holiday Promotion'
	)
)
```


### Aula 24: Resolução Exercício 6
- A empresa implementou um programa de fidelização de clientes empresariais. Todos aqueles que comprarem mais de 3000 unidades de um mesmo produto receberá descontos em outras compras. Você deverá descobrir as informações de CustomerKey e CompanyName destes clientes.

```sql
SELECT
	CustomerKey,
	CompanyName
FROM DimCustomer
WHERE CustomerKey IN (
	SELECT CustomerKey
	FROM FactOnlineSales
	GROUP BY CustomerKey, ProductKey
	HAVING COUNT(*) >= 3000
)
```


### Aula 25: Resolução Exercício 7
- Você deverá criar uma consulta para o setor de vendas que mostre as seguintes colunas da tabela DimProduct: ProductKey, ProductName, BrandName, UnitPrice, Média de UnitPrice.

```sql
SELECT
	Productkey,
	ProductName,
	BrandName,
	UnitPrice
	ROUN((SELECT AVG(UnitPrice) FROM DimProduct), 2) AS 'UnitPrice (AVG)'
FROM
	DimProcudt
```


### Aula 26: Resolução Exercício 8
- Faça uma consulta para descobrir os seguintes indicadores dos seus produtos: Maior quantidade de produtos por marca, Menor quantidade de produtos por marca e Média de produtos por marca

```sql
SELECT
	MAX(Quantidade) AS 'Máximo',
	MIN(Quantidade), AS 'Mínimo',
	AVG(Quantidade) AS 'Média'
FROM (
	SELECT
		BrandName,
		COUNT(*) AS 'Quantidade'
	FROM DimProduct
	GROUP BY BrandName
) AS T
```


### Aula 27: Resolução Exercício 9
- Crie uma CTE que seja o agrupamento da tabela DimProduct, armazenando o total de produtos por marca. Em seguida, faça um SELECT nesta CTE, descobrindo qual é a quantidade máxima de produtos para uma marca. Chame esta CTE de CTE_QtdProdutosPorMarca.

```sql
WITH CTE_QtdProdutosPorMarca AS (
	SELECT
		BrandName,
		COUNT(*) AS 'Quantidade'
	FROM DimProduct
	GROUP BY BrandName
)

SELECT MAX(Quantidade) FROM CTE_QtdProdutosPorMarca
```


### Aula 28: Resolução Exercício 10
- Crie duas CTEs.
- (i) a primeira deve conter as colunas ProductKey, ProductName, ProductSubcategoryKey, BrandName e UnitPrice, da tabela DimProduct, mas apenas os produtos da marca Adventure Works. Chame essa CTE de CTE_ProdutosAdventureWorks.
- (ii) a segunda deve conter as colunas ProductSubcategoryKey, ProductSubcategoryName, da tabela DimProductSubcategory mas apenas para as subcategorias ‘Televisions’ e ‘Monitors’. Chame essa CTE de CTE_CategoriaTelevisionsEMonitors.

```sql
WITH CTE_ProdutosAdventureWorks AS (
	SELECT
		ProductKey,
		Productname,
		ProductSubcategoryKey,
		BrandName,
		UnitPrice
	FROM DimProduct
	WHERE BrandName = 'Adventure Works'
),
CTE_CategoriaTelevisionsEMonitors AS (
	SELECT
		ProductSubcategoryKey,
		ProductSubcategoryName
	FROM DimProductSubcategory
	WHERE ProductSubcategoryName IN ('Televisions', ‘Monitors’)
)
```

- Faça um Join entre essas duas CTEs, e o resultado deve ser uma query contendo todas as colunas das duas tabelas. Observe nesse exemplo a diferença entre o LEFT JOIN e o INNER JOIN.

```sql
SELECT
	CTE_ProdutosAdventureWorks.*,
	CTE_CategoriaTelevisionsEMonitors.ProductSubcategoryName
FROM CTE_ProdutosAdventureWorks
LEFT JOIN CTE_CategoriaTelevisionsEMonitors
	ON CTE_ProdutosAdventureWorks.ProductSubcategoryKey = CTE_CategoriaTelevisionsEMonitors.ProductSubcategoryKey

SELECT
	CTE_ProdutosAdventureWorks.*,
	CTE_CategoriaTelevisionsEMonitors.ProductSubcategoryName
FROM CTE_ProdutosAdventureWorks
INNER JOIN CTE_CategoriaTelevisionsEMonitors
	ON CTE_ProdutosAdventureWorks.ProductSubcategoryKey = CTE_CategoriaTelevisionsEMonitors.ProductSubcategoryKey

-- A tabela do lado esquerdo tem mais categorias do que Televisions e Monitors, logo quando faz um left join ficar com categorias em null.

-- Renomeando as CTEs para simplificar

SELECT
	PAW.*,
	CTM.ProductSubcategoryName
FROM CTE_ProdutosAdventureWorks AS PAW
LEFT JOIN CTE_CategoriaTelevisionsEMonitors AS CTM
	ON PAW.ProductSubcategoryKey = CTM.ProductSubcategoryKey

SELECT
	PAW.*,
	CTM.ProductSubcategoryName
FROM CTE_ProdutosAdventureWorks AS PAW
INNER JOIN CTE_CategoriaTelevisionsEMonitors AS CTM
	ON PAW.ProductSubcategoryKey = CTM.ProductSubcategoryKey
```


--------------
## Módulo 16: Loops no SQL

### Aula 2: WHILE - Estrutura básica
- Crie um contador que faça uma contagem de 1 até 10 utilizando a estrutura de repetição WHILE

```sql
DECLARE @varContador INT
SET @varContador = 1

WHILE @varContador <= 10
BEGIN
	PRINT 'O valor do contador é: ' + CONVERT(VARCHAR, @varContador)
	SET @varContador = @varContador + 1
END
```


### Aula 3: WHILE - Cuidado com loops infinitos
- Cuidado com loops infinitos!!!

```sql
DECLARE @varContador INT
SET @varContador = 1

WHILE @varContador <= 5
BEGIN
	PRINT @varContador
END
```


### Aula 4: BREAK - Interrompendo um loop antes do final
- Faça um contador de 1 a 100. OBS: Se o valor do contador for igual a 15, então o loop WHILE deve ser encerrado.

```sql
DECLARE @varContador INT
SET @varContador = 1

WHILE @varContador <= 100
BEGIN
	IF @varContador = 15
	BREAK
	PRINT 'O valor do contador é: ' + CONVERT(VARCHAR, @varContador)
	SET @varContador += 1
END
```


### Aula 5: CONTINUE - Pulando repetições em um loop
- Faça um contador de 1 a 10. OBS: Os números 3 ou 6 não podem ser printados na tela

```sql
DECLARE @varContador INT
SET @varContador = 0

WHILE @varContador < 10
BEGIN
	SET @varContador += 1
	IF @varContador = 3 OR @varContador = 6
	CONTINUE
	PRINT 'O valor da variável é: ' + CONVERT(VARCHAR, @varContador)
END
```


### Aula 7: Resolução Exercício 1
- Utilize o Loop While para criar um contador que comece em um valor inicial @ValorInicial e termine em um valor final @ValorFinal. Você deverá printar na tela a seguinte frase: “O valor do contador é: “ + ___

```sql
DECLARE @ValorInicial INT, @ValorFinal INT
SET @ValorInicial = 1
SET @ValorFinal = 10

WHILE @ValorInicial <= @ValorFinal
BEGIN
	PRINT 'O valor do contador é: ' + CONVERT(VARCHAR, @ValorInicial)
	SET @varInicial += 1
END
```


### Aula 8: Resolução Exercício 2
- Você deverá criar uma estrutura de repetição que printe na tela a quantidade de contratações para cada ano, desde 1996 até 2003. A informação de data de contratação encontra-se na coluna HireDate da tabela DimEmployee. Utilize o formato:
	- X contratações em 1996
	- Y contratações em 1997
	- Z contratações em 1998
- Obs: a coluna HireDate contém a data completa (dd/mm/aaaa). Lembrando que você deverá printar a quantidade de contratações por ano.

```sql
DECLARE @AnoInicial INT = 1996
DECLARE @AnoFinal INT = 2003

WHILE @AnoInicial <= @AnoFinal
BEGIN
	DECLARE @QtdFuncionario INT = (
		SELECT COUNT(*) FROM DimEmployee
		WHERE YEAR(HireDate) = @AnoInicial
	)
	PRINT CONCAT(@QtdFuncionarios, ' contratações em ', @AnoInicial)
	SET @AnoInicial += 1
END
```


### Aula 9: Resolução Exercício 3
- Utilize um Loop While para criar uma tabela chamada Calendario, contendo uma coluna que comece com a data 01/01/2021 e vá até 31/12/2021.

```sql
CREATE TABLE Calendario (
	Data DATE
)

DECLARE @dataInicial DATE = 01/01/2021
DECLARE @dataFinal DATE = 31/12/2021

WHILE @dataInical <= @dataFinal
BEGIN
	INSERT INTO Calendario (Data) VALUES (@dataInicial)
	SET @dataInicial = DATEADD(DAY, 1, @dataInicial)
END

SELECT * FROM Calendario
```


------------
## Módulo 17: Window Functions (Funções de Janela)

### Aula 2: Código para criar a tabela Lojas

```sql
CREATE DATABASE WF
USE WF

CREATE TABLE Lojas(
   ID_Loja INT,
   Nome_Loja VARCHAR(100),
   Regiao VARCHAR(100),
   Qtd_Vendida FLOAT
)

INSERT INTO LOJAS(ID_Loja, Nome_Loja, Regiao, Qtd_Vendida)
VALUES
   (1, 'Botafogo Praia&Mar', 'Sudeste', 1800),
   (2, 'Lojas Vitoria', 'Sudeste', 800),
   (3, 'Empórioi Mineirinho', 'Sudeste', 2300),
   (4, 'Central Paulista', 'Sudeste', 1800),
   (5, 'Rio 90 graus', 'Sudeste', 700),
   (6, 'Casa Flor & Anópolis', 'Sul', 2100),
   (7, 'Pampas & Co', 'Sul', 990),
   (8, 'Paraná Papéis', 'Sul', 2800),
   (9, 'Amazonas Prime', 'Norte', 4200),
   (10, 'Pará Bens', 'Norte', 3200),
   (11, 'Tintas Rio Branco', 'Norte', 1500),
   (12, 'Nordestemido Hall', 'Nordeste', 1910),
  (13, 'Cachoerinha Loft', 'Nordeste', 2380)
```


### Aula 3: Funções de Agregação - SUM, COUNT, AVG, MIN, MAX
- Crie uma coluna contendo a SOMA total das vendas da tabela lojas.

```sql
SELECT
	ID_Loja,
	Nome_Loja,
	Regiao,
	Qtd_Vendida,
	SUM(Qtd_Vendida) OVER() AS 'Total Vendido'
FROM Lojas

-- Soma por Região
SELECT
	ID_Loja,
	Nome_Loja,
	Regiao,
	Qtd_Vendida,
	SUM(Qtd_Vendida) OVER(PARTITION BY Regiao) AS 'Total Vendido'
FROM Lojas
```

- Crie uma coluna contendo a CONTAGEM das vendas da tabela lojas

```sql
SELECT
	ID_Loja,
	Nome_Loja,
	Regiao,
	Qtd_Vendida,
	COUNT(*) OVER() AS 'Qtd. Lojas'
FROM Lojas

-- Contagem por Região
SELECT
	ID_Loja,
	Nome_Loja,
	Regiao,
	Qtd_Vendida,
	COUNT(*) OVER(PARTITION BY Regiao) AS 'Qtd. Lojas'
FROM Lojas
```

- Crie uma coluna contendo a MÉDIA das vendas da tabela lojas

```sql
SELECT
	ID_Loja,
	Nome_Loja,
	Regiao,
	Qtd_Vendida,
	AVG(Qtd_Vendida) OVER() AS 'Média Lojas'
FROM Lojas

-- Média por Região
SELECT
	ID_Loja,
	Nome_Loja,
	Regiao,
	Qtd_Vendida,
	AVG(Qtd_Vendida) OVER(PARTITION BY Regiao) AS 'Média Lojas'
FROM Lojas
```

- Crie uma coluna contendo o MIN/MAX das vendas da tabela lojas

```sql
-- MIN
SELECT
	ID_Loja,
	Nome_Loja,
	Regiao,
	Qtd_Vendida,
	MIN(Qtd_Vendida) OVER() AS 'Menor venda'
FROM Lojas

-- Menor venda por Região
SELECT
	ID_Loja,
	Nome_Loja,
	Regiao,
	Qtd_Vendida,
	MIN(Qtd_Vendida) OVER(PARTITION BY Regiao) AS 'Menor venda'
FROM Lojas


-- MAX
SELECT
	ID_Loja,
	Nome_Loja,
	Regiao,
	Qtd_Vendida,
	MAX(Qtd_Vendida) OVER() AS 'Maior venda'
FROM Lojas

-- Menor venda por Região
SELECT
	ID_Loja,
	Nome_Loja,
	Regiao,
	Qtd_Vendida,
	MAX(Qtd_Vendida) OVER(PARTITION BY Regiao) AS 'Maior venda'
```


### Aula 4: Calculando percentual de participação (Parte 1)
- a) Calcule o % de participação de cada loja em relação ao total de vendas de todas as lojas.

```sql
SELECT
	ID_Loja,
	Nome_Loja,
	Regiao,
	Qtd_Vendida,
	SUM(Qtd_Vendida) OVER() AS 'Total Vendido',
	FORMAT(Qtd_Vendida)/(SUM(Qtd_Vendida) OVER() AS 'Total Vendido'), '0.00%') AS '% do Total'
FROM Lojas
ORDER BY ID_Loja
```


### Aula 5: Calculando percentual de participação (Parte 2)
- b) Calcule o % de participacao de cada loja em relação ao total de vendas de cada região.

```sql
SELECT
	ID_Loja,
	Nome_Loja,
	Regiao,
	Qtd_Vendida,
	SUM(Qtd_Vendida) OVER(PARTITION BY Regiao) AS 'Total Vendido',
	FORMAT(Qtd_Vendida)/(SUM(Qtd_Vendida) OVER(PARTITION BY Regiao) AS 'Total Vendido'), '0.00%') AS '% do Total'
FROM Lojas
ORDER BY ID_Loja
```


### Aula 6: Funções de Classificação - ROW_NUMBER, RANK, DENSE_RANK, NTILE

```sql
SELECT
	ID_Loja,
	Nome_Loja,
	Regiao,
	Qtd_Vendida,
	ROW_NUMBER() OVER(ORDER BY Qtd_Vendida DESC) AS 'rownumber',
	RANK() OVER(ORDER BY Qtd_Vendida DESC) AS 'rank',
	DENSE_RANK() OVER(ORDER BY Qtd_Vendida DESC) AS 'dense',
	NTILE(2) OVER(ORDER BY Qtd_Vendida DESC) AS 'ntile'
FROM Lojas
```


### Aula 7: Funções de Classificação mais PARTITION BY

```sql
SELECT
	ID_Loja,
	Nome_Loja,
	Regiao,
	Qtd_Vendida,
	ROW_NUMBER() OVER(PARTITION BY Regiao ORDER BY Qtd_Vendida DESC) AS 'rownumber',
	RANK() OVER(PARTITION BY Regiao ORDER BY Qtd_Vendida DESC) AS 'rank',
	DENSE_RANK() OVER(PARTITION BY Regiao ORDER BY Qtd_Vendida DESC) AS 'dense',
	NTILE(2) OVER(PARTITION BY Regiao ORDER BY Qtd_Vendida DESC) AS 'ntile'
FROM Lojas
ORDER BY ID_Lojas
```


### Aula 8: RANK mais GROUP BY
- Crie uma tabela com o total de vendas por região e adicione uma coluna de ranking nessa tabela.

```sql
SELECT
	Regiao AS 'Região',
	SUM(Qtd_Vendida) AS 'Total Vendida',
	RANK() OVER(ORDER BY SUM(Qtd_Vendida) DESC) AS 'Ranking'
FROM
	Lojas
GROUP BY Regiao
ORDER BY [Total Vendido] DESC
```


### Aula 9: Cálculo de soma móvel e média móvel

```sql
CREATE TABLE Resultado(
Data_Fechamento DATETIME,
Mes_Ano VARCHAR(100),
Faturamento_MM FLOAT)


INSERT INTO Resultado(Data_Fechamento, Mes_Ano, Faturamento_MM)
VALUES
	('01/01/2020', 'JAN-20', 8),
	('01/02/2020', 'FEV-20', 10),
	('01/03/2020', 'MAR-20', 6),
	('01/04/2020', 'ABR-20', 9),
	('01/05/2020', 'MAI-20', 5),
	('01/06/2020', 'JUN-20', 4),
	('01/07/2020', 'JUL-20', 7),
	('01/08/2020', 'AGO-20', 11),
	('01/09/2020', 'SET-20', 9),
	('01/10/2020', 'OUT-20', 12),
	('01/11/2020', 'NOV-20', 11),
	('01/12/2020', 'DEZ-20', 10)

SELECT * FROM Resultado
```

- Soma móvel

```sql
SELEC
	Data_Fechamento,
	Mes_Ano,
	Faturamento_MM,
	SUM(Faturamento_MM) OVER(ORDER BY Data_Fechamento ROWS BETWEEN 1 PRECEDING AND CURRENT ROW) AS 'Soma móvel'
FROM
	Resultado
```

- Média móvel

```sql
SELEC
	Data_Fechamento,
	Mes_Ano,
	Faturamento_MM,
	AVG(Faturamento_MM) OVER(ORDER BY Data_Fechamento ROWS BETWEEN 1 PRECEDING AND CURRENT ROW) AS 'Média móvel'
FROM
	Resultado
```


### Aula 10: Cálculo de acumulado
- Soma acumulada

```sql
SELEC
	Data_Fechamento,
	Mes_Ano,
	Faturamento_MM,
	SUM(Faturamento_MM) OVER(ORDER BY Data_Fechamento ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS 'Acumulado'
FROM
	Resultado
```


### Aula 11: Um pouco mais sobre soma móvel e acumulado

```sql
SELEC
	Data_Fechamento,
	Mes_Ano,
	Faturamento_MM,
	SUM(Faturamento_MM) OVER(ORDER BY Data_Fechamento ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING) AS 'Soma móvel'
FROM
	Resultado
```


### Aula 12: Funções de Offset (Deslocamento) - LAG e LEAD

```sql
SELECT
	Data_Fechamento,
	Mes_Ano,
	Faturamento_MM,
	LAG(Faturamento_MM, 1, 0) OVER(ORDER BY Data_Fechamento) AS 'Lag',
	LEAD(Faturamento_MM, 1, 0) OVER(ORDER BY Data_Fechamento) AS 'Lead'
FROM Resultado
```


### Aula 13: Cálculo MoM (Parte 1)

```sql
SELECT
	Data_Fechamento,
	Mes_Ano,
	Faturamento_MM,
	FORMAT((Faturamento_MM/LAG(Faturamento_MM, 1) OVER(ORDER BY Data_Fechamento)) -1, '0.00%') AS ' % MoM'
FROM Resultado
```


### Aula 14: Cálculo MoM (Parte 2)

```sql
SELECT
	Data_Fechamento,
	Mes_Ano,
	Faturamento_MM,
	FORMAT((Faturamento_MM/NULLIF(LAG(Faturamento_MM, 1) OVER(ORDER BY Data_Fechamento), 0)) -1, '0.00%') AS ' % MoM'
FROM Resultado
```


### Aula 15: Funções de Offset (Deslocamento) - FIRST_VALUE e LAST_VALUE

```sql
SELECT
	Data_Fechamento,
	Mes_Ano,
	Faturamento_MM,
	FIRST_VALUE(Faturamento_MM) OVER(ORDER BY Data_Fechamento) AS 'Primeiro valor',
	LAST_VALUE(Faturamento_MM) OVER(ORDER BY Data_Faturamento ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUDEND FOLLOWING) AS 'Último valor'
FROM Resultado
ORDER BY Data_Fechamento
```


### Aula 17: Resolução Exercício 1

```sql
CREATE VIEW vwProdutos AS
SELECT
	BrandName AS 'Marca',
	ColorName AS 'Cor',
	COUNT(*) AS 'Quantidade_Vendida',
	ROUND(SUM(SalesAmount), 2) AS 'Receita_Total'
FROM DimProduct
INNER JOIN FactSales
	ON DimProduct.ProductKey = FactSales.ProductKey
GROUP BY BrandName, ColorName
```

- Utilize a View vwProdutos para criar uma coluna extra calculando a quantidade total vendida dos produtos.

```sql
SELECT
	*,
	SUM(Quantidade_Vendida) OVER() AS 'Qtd Total Produtos'
FROM vwProdutos
ORDER BY Marca
```


### Aula 18: Resolução Exercício 2

```sql
CREATE VIEW vwProdutos AS
SELECT
	BrandName AS 'Marca',
	ColorName AS 'Cor',
	COUNT(*) AS 'Quantidade_Vendida',
	ROUND(SUM(SalesAmount), 2) AS 'Receita_Total'
FROM DimProduct
INNER JOIN FactSales
	ON DimProduct.ProductKey = FactSales.ProductKey
GROUP BY BrandName, ColorName
```

- Crie mais uma coluna na consulta anterior, incluindo o total de produtos vendidos para cada marca.

```sql
SELECT
	*,
	SUM(Quantidade_Vendida) OVER() AS 'Qtd Total Produtos',
	SUM(Quantidade_Vendida) OVER(PARTITION BY Marca) AS 'Qtd Total Vendica (por Marca)'
FROM vwProdutos
ORDER BY Marca
```


### Aula 19: Resolução Exercício 3

```sql
CREATE VIEW vwProdutos AS
SELECT
	BrandName AS 'Marca',
	ColorName AS 'Cor',
	COUNT(*) AS 'Quantidade_Vendida',
	ROUND(SUM(SalesAmount), 2) AS 'Receita_Total'
FROM DimProduct
INNER JOIN FactSales
	ON DimProduct.ProductKey = FactSales.ProductKey
GROUP BY BrandName, ColorName
```

- Calcule o % de participação do total de vendas de produtos por marca. Ex: A marca A. Datum teve uma quantidade total de vendas de 199.041 de um total de 3.406.089 de vendas. Isso significa que a da marca A. Datum é 199.041/3.406.089 = 5,84%.

```sql
SELECT
	*,
	SUM(Quantidade_Vendida) OVER() AS 'Qtd Total Produtos',
	SUM(Quantidade_Vendida) OVER(PARTITION BY Marca) AS 'Qtd Total Vendica (por Marca)',
	FORMAT(1.0*SUM(Quantidade_Vendida) OVER(PARTITION BY Marca)/(SUM(Quantidade_Vendida) OVER()), '0.00%') AS '% Participação'
FROM vwProdutos
ORDER BY Marca
```


### Aula 20: Resolução Exercício 4

```sql
CREATE VIEW vwProdutos AS
SELECT
	BrandName AS 'Marca',
	ColorName AS 'Cor',
	COUNT(*) AS 'Quantidade_Vendida',
	ROUND(SUM(SalesAmount), 2) AS 'Receita_Total'
FROM DimProduct
INNER JOIN FactSales
	ON DimProduct.ProductKey = FactSales.ProductKey
GROUP BY BrandName, ColorName
```

- Crie uma consulta à View vwProdutos, selecionando as colunas Marca, Cor, Quantidade_Vendida e também criando uma coluna extra de Rank para descobrir a posição de cada Marca/Cor. Você deve obter o resultado abaixo. Obs: Sua consulta deve ser filtrada para que seja mostrada apenas a marca Contoso.
![image](https://github.com/user-attachments/assets/a8914170-2de3-49c2-94a3-a61135c667f7)


```sql
SELECT
	Marca,
	Cor,
	Quantidade_Vendida,
	RANK() OVER(ORDER BY Quantidade_Vendida DESC) AS 'Rank'
FROM vwProdutos
WHERE Marca = 'Contoso'
```

### Aula 21: Resolução Desafio 1
- Para responder os próximos 2 exercícios, você precisará criar uma View auxiliar. Diferente do que foi feito anteriormente, você não terá acesso ao código dessa view antes do gabarito. A sua view deve se chamar vwHistoricoLojas e deve conter um histórico com a quantidade de lojas abertas a cada Ano/Mês. Os desafios são:
	- (1) Criar uma coluna de ID para essa View
	- (2) Relacionar as tabelas DimDate e DimStore
- Dicas:
	- 1- A coluna de ID será criada a partir de uma função de janela. Você deverá se atentar a forma como essa coluna deverá ser ordenada, pensando que queremos visualizar uma ordem de Ano/Mês que seja: 2005/january, 2005/February... e não 2005/April, 2005/August...
	- 2- As colunas Ano, Mês e Qtd_Lojas correspondem, respectivamente, às seguintes colunas: CalendarYear e CalendarMonthLabel da tabela DimDate e uma contagem da coluna OpenDate da tabela DimStore.

 ```sql
CREATE VIEW vwHistoricoLojas AS
SELECT
	ROW_NUMBER() OVER(ORDER BY CalendarMonth) AS 'ID',
	CalendarYear AS 'Ano',
	CalendarMonthLabel AS 'Mês',
	COUNT(OpenDate) AS 'Qtd_Lojas'
FROM DimDate
LEFT JOIN DimStore
	ON DimDate.Datekey = DimStore.OpenDate
GROUP BY CalendarYear, CalendarMonthLabel, CalendarMonth
```


### Aula 22: Resolução Exercício 5
- A partir da view criada no exercício anterior, você deverá fazer uma soma móvel considerando sempre o mês atual + 2 meses para trás.

```sql
SELECT
	*,
	SUM(Qtd_Lojas) OVER(ORDER BY ID ROWS BETWEEN 2 PRECEDING AND CURRENT ROW)
FROM vwHistoricoLojas
```


### Aula 23: Resolução Exercício 6
- Utilize a vwHistoricoLojas para calcular o acumulado de lojas abertas a cada ano/mês.

```sql
SELECT
	*,
	SUM(Qtd_Lojas) OVER(ORDER BY ID ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
FROM vwHistoricoLojas
```

### Aula 24: Resolução Desafio 2
- Neste desafio, você terá que criar suas próprias tabelas e views para conseguir resolver os exercícios 7 e 8. Os próximos exercícios envolverão análises de novos clientes. Para isso, será necessário criar uma nova tabela e uma nova view. Abaixo, temos um passo a passo para resolver o problema por partes.
	- PASSO 1: Crie um novo banco de dados chamado Desafio e selecione esse banco de dados criado.
	- PASSO 2: Crie uma tabela de datas entre o dia 1 de janeiro do ano com a compra (DateFirstPurchase) mais antiga e o dia 31 de dezembro do ano com a compra mais recente. Obs1: Chame essa tabela de Calendario. Obs2: A princípio, essa tabela deve conter apenas 1 coluna, chamada data e do tipo DATE.
	- PASSO 3: Crie colunas auxiliares na tabela Calendario chamadas: Ano, Mes, Dia, AnoMes e NomeMes. Todas do tipo INT.
	- PASSO 4: Adicione na tabela os valores de Ano, Mês, Dia, AnoMes e NomeMes (nome do mês em português). Dica: utilize a instrução CASE para verificar o mês e retornar o nome certo.
	- PASSO 5: Crie a View vwNovosClientes, que deve ter as colunas mostradas abaixo.

```sql
-- Passo 1
CREATE DATABASE Desafio
USE Desafio

-- Passo 2
CREATE TABLE Calendario (
	data DATE
)

DECLARE @varAnoInicial INT = YEAR(SELECT MIN(DateFirstPurchase) FROM ContosoRetailDW.dbo.DisCustomer)
DECLARE @varAnoFinal INT = YEAR(SELECT MAX(DateFirstPurchase) FROM ContosoRetailDW.dbo.DisCustomer)

DECLARE @varDataInicial DATE = DATEFROMPARTS(@varAnoInicial, 1, 1)
DECLARE @varDataFinal DATE = DATEFROMPARTS(@varAnoFinal, 12, 31)

WHILE @varDataInicial <= @varDataFinal
BEGIN
	INSERT INTO Calendario(data) VALUES(@varDataInicial)
	SET @varDataInicial = DATEADD(DAY, 1, @varDataFinal)
END

-- Passo 3
ALTER TABLE Calendario
ADD Ano INT,
	Mes INT,
	Dia INT,
	AnoMes INT,
	NomeMes VARCHAR(50)

-- Passo 4
UPDATE Calendario SET Ano = YEAR(data)
UPDATE Calendario SET Mes = MONTH(data)
UPDATE Calendario SET Dia = DAY(data)
UPDATE Calendario SET AnoMes = CONCAT(YEAR(data), FORMAT(MONTH(data), '00'))
UPDATE Calendario SET NomeMes =
	CASE
		WHEN MONTH(data) = 1 THEN 'Janeiro'
		WHEN MONTH(data) = 2 THEN 'Feveiro'
		WHEN MONTH(data) = 3 THEN 'Março'
		WHEN MONTH(data) = 4 THEN 'Abril'
		WHEN MONTH(data) = 5 THEN 'Maio'
		WHEN MONTH(data) = 6 THEN 'Junho'
		WHEN MONTH(data) = 7 THEN 'Julho'
		WHEN MONTH(data) = 8 THEN 'Agosto'
		WHEN MONTH(data) = 9 THEN 'Setembro'
		WHEN MONTH(data) = 10 THEN 'Outubro'
		WHEN MONTH(data) = 11 THEN 'Novembro'
		WHEN MONTH(data) = 12 THEN 'Dezembro'
	END

-- Passo 5
CREATE VIEW vwNovosClientes AS
SELECT
	ROW_NUMBER() OVER(ORDER BY AnoMes) AS 'ID',
	Ano,
	NomeMes,
	COUNT(DimCustomer.DateFirstPurchase) AS 'Novos_Clientes'
FROM Calendario
LEFT JOIN ContosoRetailDW.dbo.DimCustomer
	ON Calendario.data = DimCustomer.DateFirstPurchase
GROUP BY Ano, NomeMes, AnoMes
```


### Aula 25: Resolução Exercício 7
- a) Faça um cálculo de soma móvel de novos clientes nos últimos 2 meses.

```sql
SELECT
	*,
	SUM(Novos_Clientes) OVER(ORDER BY ID ROWS BETWEEN 2 PRECEDING AND CURRENT ROW) AS 'Soma Móvel (2 meses)'
FROM vwNovosClientes
```

- b) Faça um cálculo de média móvel de novos clientes nos últimos 2 meses.

```sql
SELECT
	*,
	AVG(Novos_Clientes) OVER(ORDER BY ID ROWS BETWEEN 2 PRECEDING AND CURRENT ROW) AS 'Média Móvel (2 meses)'
FROM vwNovosClientes
```

- c) Faça um cálculo de acumulado dos novos clientes ao longo do tempo.

```sql
SELECT
	*,
	SUM(Novos_Clientes) OVER(ORDER BY ID ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS 'Acumulado Total'
FROM vwNovosClientes
```

- d) Faça um cálculo de acumulado intra-ano, ou seja, um acumulado que vai de janeiro a dezembro de cada ano, e volta a fazer o cálculo de acumulado no ano seguinte.

```sql
SELECT
	*,
	SUM(Novos_Clientes) OVER(PARTITION BY Ano ORDER BY ID ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS 'Acumulado YTD'
FROM vwNovosClientes
```


### Aula 26: Resolução Exercício 8
- Faça os cálculos de MoM e YoY para avaliar o percentual de crescimento de novos clientes, entre o mês atual e o mês anterior, e entre um mês atual e o mesmo mês do ano anterior.

```sql
SELECT
	*,
	LAG(Novos_Clientes, 1) OVER(ORDER BY ID),
	FORMAT(Novos_Clientes/NULLIF(LAG(Novos_Clientes, 1) OVER(ORDER BY ID), 0) - 1, '00.0%') AS '% MoM',
	FORMAT(Novos_Clientes/NULLIF(LAG(Novos_Clientes, 12) OVER(ORDER BY ID), 0) - 1, '00.0%') AS '% YoY'
FROM vwNovosClientes
```


-----------
## Módulo 19: Regex - Regular Expressions

### Aula 3: Um pouco mais sobre COLLATE

```sql
-- O que é? O COLLATION nos permite configurar se teremos diferenciação entre maiúsculas e minúsculas, ou entre palavras acentuadas.

-- O COLLATION pode ser definido em níveis diferentes no SQL Server. a nível SQL Server, a nível de banco de dados e a nível de tabelas/colunas.

-- 1. A nível SQL Server
-- O COLLATION padrão é Latin1_General_CI_AS
-- Para descobrir o COLLATION configurado:

SELECT SERVERPROPERTY('collation')

-- 2. A nível de Banco de Dados
-- Herdam o COLLATION do SQL Server. Podemos especificar na criação do Banco de Dados.

CREATE DATABASE BD_Collation
COLLATE Latin'_General_CS_AS

-- Podemos alterar o COLLATE após criar o banco de dados.

ALTER DATABASE BD_Collation COLLATE Latin1_General_CI_AS

-- Saber o COLLATION de um banco de dados específico.

SELECT DATABASEPROPERTYEX('BD_Collation', 'collation')

-- 3. A nível de Coluna/Tabela
-- Herda o COLLATION do banco de dados.
-- Criando uma coluna com um COLLATION diferente.

CREATE TABLE Nomes(
	ID INT,
	Nome VARCHAR(100) COLLATE Latin1_General_CS_AS
)

-- Podemos ver o COLLATION de cada coluna.

sp_help Nomes
```


### Aula 4: COLLATE - Exemplo

```sql
CREATE DATABASE bd_Collation
COLLATE Latin1_General_CI_AS

CREATE TABLE Tabela(
	ID INT,
	Nome VARCHAR(100) COLLATE Latin1_General_CS_AS
)

INSERT INTO Tabela(ID, Nome)
VALUES
	(1, 'Matheus'), (2, 'Marcela'), (3, 'marcos), (4, 'MAuricio'), (5, 'Marta'), (6, 'Miranda'), (7, 'Melissa'), (8, 'Lucas'), (9, 'luisa'), (10, 'Pedro')

SELECT
	ID,
	Nome
FROM Tabela
WHERE Nome = 'marcela' -- não mostra nada pios é case sensitive

SELECT
	ID,
	Nome
FROM Tabela
WHERE Nome COLLATE Latin1_General_CI_AS = 'marcela' -- se tornou case insensitive
```


### Aula 5: LIKE - Case sensitive

```sql
CREATE TABLE Tabela(
	ID INT,
	Nome VARCHAR(100) COLLATE Latin1_General_CS_AS
)

INSERT INTO Tabela(ID, Nome)
VALUES
	(1, 'Matheus'), (2, 'Marcela'), (3, 'marcos), (4, 'MAuricio'), (5, 'Marta'), (6, 'Miranda'), (7, 'Melissa'), (8, 'Lucas'), (9, 'luisa'), (10, 'Pedro')

-- LIKE padrão como aprendemos até agora.
SELECT *
FROM Names
WHERE Nome LIKE 'mar%'

-- Retorna as linhas onde a primeira letra seja 'm', a segunda seja 'a' e a terceira seja 'r'.
SELECT *
FROM Names
WHERE Nome LIKE '[m][a][r]%'

-- Retorna as linhas onde a primeira letra seja 'M', a segunda seja 'a' e a terceira seja 'r'.
SELECT *
FROM Names
WHERE Nome LIKE '[M][a][r]%'

-- Retorna as linhas onde a primeira letra seja 'M' ou 'm', e a segunda seja 'A' ou 'a'.
SELECT *
FROM Names
WHERE Nome LIKE '[Mm][Aa]%'
```


### Aula 6: LIKE - Filtrando os primeiros caracteres mais Case sensitive

```sql
USE BD_Collation
CREATE TABLE Textos(
	ID INT,
	Texto VARCHAR(100) COLLATE Latin1_General_CS_AS
)

INSERT INTO Textos(ID, Texto)
VALUES
	(1, 'Marcos'), (2, 'Excel'), (3, 'leandro'), (4, 'K'), (5, 'X7'), (6, '19'), (7, '#M'), (8, '@9'), (9,'M'), ('0,'RT')

-- Retornando nomes que começam com a letra 'M', 'E' ou 'K'
SELECT *
FROM Textos
WHERE Texto LIKE '[MEK]%'

-- Retornando nomes que possuem apenas 1 caracter
SELECT *
FROM Textos
WHERE Tecto LIKE '[A-z]'

-- Retornando nomes que possuem apenas 2 caracteres
SELECT *
FROM Textos
WHERE Tecto LIKE '[A-z][A-z]'

-- Retornando nomes que possuem apenas 2 caracteres: o primeiro uma letra e o segundo um número
SELECT *
FROM Textos
WHERE Tecto LIKE '[A-z][0-9]'
```


### Aula 7: LIKE - Filtrando mais personalizado e caractere curinga

```sql
CREATE TABLE Tabela(
	ID INT,
	Nome VARCHAR(100) COLLATE Latin1_General_CS_AS
)

INSERT INTO Tabela(ID, Nome)
VALUES
	(1, 'Matheus'), (2, 'Marcela'), (3, 'marcos), (4, 'MAuricio'), (5, 'Marta'), (6, 'Miranda'), (7, 'Melissa'), (8, 'Lucas'), (9, 'luisa'), (10, 'Pedro')

-- Retorna os nomes que:
-- 1. Começam com a letra 'M' ou 'm'
-- 2. O segundo caractere pode ser qualuer coisa ('_' é um coringa)
-- 3. O terceiro caractere pode ser a letra 'R' ou a letra 'r'
-- 4. Possui uma quantidade qualquer de caracteres depois do terceiro (por conta do %)

SELECT *
FROM Nomes
WHERE Nome LIKE '[Mm]_[Rr]%'
```


### Aula 8: LIKE - Utilizando o operador de negação

```sql
CREATE TABLE Tabela(
	ID INT,
	Nome VARCHAR(100) COLLATE Latin1_General_CS_AS
)

INSERT INTO Tabela(ID, Nome)
VALUES
	(1, 'Matheus'), (2, 'Marcela'), (3, 'marcos), (4, 'MAuricio'), (5, 'Marta'), (6, 'Miranda'), (7, 'Melissa'), (8, 'Lucas'), (9, 'luisa'), (10, 'Pedro')

-- Retorna nomes que não começa com as letras 'L' ou 'l'
SELECT *
FROM Nomes
WHERE Nome LIKE '[^Ll]%'

-- Retorna nomes que começam com qualquer caractere (caractere curinga) e a segunda letra não é um 'E' ou 'e'
SELECT *
FROM Nomes
WHERE Nome LIKE '_[^Ee]%'
```


### Aula 9 de 10: LIKE - Filtrando caracteres especiais

```sql
USE BD_Collation
CREATE TABLE Textos(
	ID INT,
	Texto VARCHAR(100) COLLATE Latin1_General_CS_AS
)

INSERT INTO Textos(ID, Texto)
VALUES
	(1, 'Marcos'), (2, 'Excel'), (3, 'leandro'), (4, 'K'), (5, 'X7'), (6, '19'), (7, '#M'), (8, '@9'), (9,'M'), ('0,'RT')

-- Identificando caracteres esperciais
SELECT *
FROM Textos
WHERE Texto LIKE '%[^a-z0-9]%'
```


### Aula 10 de 10: LIKE - Filtros especiais com números

```sql
USE BD_Collation
CREATE TABLE Numero(
	Numero DECIMAL(20, 2)
)

INSERT INTO Numeros(Numero)
VALUES
	(50), (30.23), (9), (100.54), (15.9), (6.5), (10), (501.76), (1000.56), (31)

-- Retornando os números que possuem 2 dígitos na parte inteira
SELECT *
FROM Numeros
WHERE Numero LIKE '[0-9][0-9].[0][0]'

-- Retorando linhas que:
-- 1. Possuem 3 dígitos na parte inteira, sendo o primeiro dígito igual a 5
-- 2. O primeiro número da parte decimal seja 7
-- 3. O segundo número da parte decimal seja um número entre 0 e 9

SELECT *
FROM Numeros
WHERE Numero LIKE '[5]_.[7][0-9]'
```


------------
## Módulo 20: Constraints

### Aula 2: NOT NULL, UNIQUE, CHECK, DEFAULT, IDENTITY, PRIMARY KEY, FOREIGN KEY

```sql
-- I. CONSTRAINTS
-- Constraints no SQL são regras (restrições) que podemos definir para uma coluna de uma tabela.
-- Abaixo temos uma lista de restrições:

-- 1. NOT NULL
-- 2. UNIQUE
-- 3. CHECK
-- 4. DEFAULT
-- 5. IDENTITY
-- 6. PRIMARY KEY
-- 7. FOREIGN KEY



-- 1. NOT NULL
-- Essa constraint não permite que sejam adicionados valores nulos na coluna.


-- 2. UNIQUE
-- Identifica uma coluna de forma única, sem permitir valores duplicados (mas, permite NULL).


-- 3. CHECK
-- Verifica se o valor adicionado na coluna atende a uma determinada condição.


-- 4. DEFAULT
-- Retorna um valor default caso a coluna não seja preenchida.


-- 5. IDENTITY
-- Permite que uma coluna siga uma auto numeração (usada em colunas de ID).


-- 6. PRIMARY KEY
-- Uma CHAVE PRIMÁRIA (PRIMARY KEY) é uma coluna que identifica de forma única as linhas 
-- de uma tabela. Nenhum dos valores de uma coluna de chave primária deve ser nulo ou se repetir.
-- Será através dessa coluna que criaremos relações entre as tabelas.

-- 7. FOREIGN KEY
-- Uma CHAVE ESTRANGEIRA (FOREIGN KEY) é uma coluna que será relacionada com a CHAVE PRIMÁRIA
-- de uma outra tabela.
```


## Aula 4: Criando Constraints para a Tabela dCliente

```sql
CREATE DATABASE Exercicios
USE Exercicios

-- Tabela 1: dCliente

-- A tabela dCliente deve conter as seguintes colunas:

-- Coluna 1: id_cliente do tipo INT          --> Chave Primária e deve ser auto incrementada
-- Coluna 2: nome_cliente do tipo VARCHAR    --> Não aceita valores nulos
-- Coluna 3: genero VARCHAR                  --> Não aceita valores nulos e devem ser ('M', 'F', 'O', 'PND')
-- Coluna 4: data_nascimento DATE            --> Não aceita valores nulos  
-- Coluna 5: cpf do tipo VARCHAR             --> Não aceita valores duplicados nem valores nulos

CREATE TABLE dCLiente (
	id_cliente INT IDENTITY(1, 1),
	genero VARCHAR(100) NOT NULL,
	data_nascimento DATE NOT NULL,
	cpf VARCHAR(100) NOT NULL,
	CONSTRAINT dcliente_id_cliente_pk PRIMARY KEY(id_cliente),
	CONSTRAINT dcliente_genero_ck CHECK(genero IN ('M', 'F', 'O', 'PND')),
	CONSTRAINT dcliente_cpf_un UNIQUE(cpf)
)

INSERT INTO dCliente(Nome_Cliente, Genero, Data_de_Nascimento, CPF)
VALUES
	('André Martins',  'M',  '12/02/1989', '839.283.190-00'),
	('Bárbara Campos',  'F', '07/05/1992', '351.391.410-02'),
	('Carol Freitas',  'F',  '23/04/1985', '139.274.921-12'),
	('Diego Cardoso',   'M', '11/10/1994', '192.371.081-17'),
	('Eduardo Pereira', 'M', '09/11/1988', '193.174.192-82'),
	('Fabiana Silva',  'F',  '02/09/1989', '231.298.471-98'),
	('Gustavo Barbosa', 'M', '27/06/1993', '240.174.171-76'),
	('Helen Viana',    'F',  '11/02/1990', '193.129.183-01'),
	('Igor Castro',    'M',  '21/08/1989', '184.148.102-29'),
	('Juliana Pires',   'F', '13/01/1991', '416.209.192-47')
```


### Aula 5: Criando Constraints para a Tabela dGerente

```sql
-- Tabela 2: dGerente

-- A tabela dGerente deve conter as seguintes colunas:

-- Coluna 1: id_gerente do tipo INT            --> Chave Primária e auto incrementada
-- Coluna 2: nome_gerente do tipo VARCHAR      --> Não aceita valores nulos
-- Coluna 3: data_contratacao VARCHAR          --> Não aceita valores nulos
-- Coluna 4: salario do tipo FLOAT             --> Não aceita valores nulos nem abaixo de zero

CREATE TABLE dGerente(
	id_gerente INT IDENTITY(1, 1),
	nome_gerente VARCHAR(100) NOT NULL,
	data_contratacao VARCHAR(100) NOT NULL,
	salario FLOAT NOT NULL
	CONSTRAINT dgerente_id_gerente_pk PRIMARY KEY(id_gerente),
	CONSTRAINT dgerente_salario_ck CHECK(salario > 0)
)

INSERT INTO dGerente(Nome_Gerente, Data_Contratacao, Salario)
VALUES
	('Lucas Sampaio',   '21/03/2015', 6700),
	('Mariana Padilha', '10/01/2011', 9900),
	('Nathália Santos', '03/10/2018', 7200),
	('Otávio Costa',    '18/04/2017', 11000)
```


### Aula 6: Criando Constraints para a Tabela fContratos

```sql
-- Tabela 3: fContratos

-- A tabela fContratos deve conter as seguintes colunas:

-- Coluna 1: id_contrato do tipo INT           --> Chave Primária e auto incremental
-- Coluna 2: data_assinatura do tipo DATE      --> Valor Padrão (GETDATE) caso não seja preenchida
-- Coluna 3: id_cliente do tipo INT            --> Chave Estrangeira
-- Coluna 4: id_gerente do tipo INT            --> Chave Estrangeira
-- Coluna 5: valor_contrato do tipo FLOAT      --> Não aceita valores nulos e deve ser maior que zero

CREATE TABLE fContratos(
	id_contrato INT IDENTITY(1, 1),
	data_assinatura DATE DEFAULT GETDATE(),
	id_cliente INT,
	id_gerente INT,
	valor_contrato FLOAT NOT NULL,
	CONSTRAINT fcontratos_id_contrato_pk PRIMARY KEY(id_contrato),
	CONTRAINT fcontratos_id_cliente_fk FOREING KEY(id_cliente) REFERENCES dCliente(id_cliente),
	CONSTRAINT dcontratos_id_gerente_fk FOREIGN KEY(id_gerente) REFERENCES dGerente(id_gerente),
	CONSTRAINT fcontratos_valor_contrato_ck CHECK(valor_contrato > 0)
)

INSERT INTO fContratos(Data_Assinatura, ID_Cliente, ID_Gerente, Valor_Contrato)
VALUES
	('12/01/2019', 8, 1, 23000),
	('10/02/2019', 3, 2, 15500),
	('07/03/2019', 7, 2, 6500),
	('15/03/2019', 1, 3, 33000),
	('21/03/2019', 5, 4, 11100),
	('23/03/2019', 4, 2, 5500),
	('28/03/2019', 9, 3, 55000),
	('04/04/2019', 2, 1, 31000),
	('05/04/2019', 10, 4, 3400),
	('05/04/2019', 6, 2, 9200)
```


### Aula 11: Gerenciando Constraints

```sql
-- 1. Adicionar constraints
-- 2. Renomear constraints
-- 3. Remover constraints

-- Remova a constraint PK da tabela fContratos.
ALTER TABLE fContratos
DROP CONSTRAINT fcontratos_id_contrato_pk

-- Remova a constraint FK Cliente da tabela fContratos.
ALTER TABLE fContratos
DROP CONSTRAINT fcontrato_id_cliente_fk

-- Adicione a constraint PK id_contrato na tabela fContratos.
ALTER TABLE fContratos
ADD CONSTRAINT fcontratos_id_contrato_pk PRIMARY KEY(id_contrato)

-- Adicione a constraint FK id_cliente na tabela fContratos.
ALTER TABLE fContratos
ADD CONSTRAINT fcontratos_id_cliente_fk FOREIGN KEY(id_cliente) REFERENCES dCliente(id_cliente)
```


### Aula 13: Resolução Exercício 1
-  Você está responsável por criar um Banco de Dados com algumas tabelas que vão armazenar informações associadas ao aluguel de carros de uma locadora.
- a) O primeiro passo é criar um banco de dados chamado AlugaFacil.

```sql
CREATE DATABASE AlugaFacil
USE AlugaFacil
```

- b) O seu banco de dados deve conter 3 tabelas e a descrição de cada uma delas é mostrada abaixo. Obs: você identificará as restrições das tabelas a partir de suas descrições.
- Tabela 1: Cliente
	- id_cliente (deve ser a chave primária da tabela, além de ser autoincrementada de forma automática)
	- nome_cliente (não aceita valores nulos)
	- cnh (não aceita valores nulos e duplicados)
	- cartao (não aceita valores nulos)

```sql
CREATE TABLE Cliente(
	id_cliente INT IDENTITY(1, 1),
	nome_cliente VARCHAR(100) NOT NULL,
	cnh VARCHAR(100) NOT NULL,
	cartao VARCHAR(100) NOT NULL,
	CONSTRAINT cliente_id_cliente_pk PRIMARY KEY(id_cliente),
	CONSTRAINT cliente_cnh_un UNIQUE(cnh)
)
```

- Tabela 2: Carro
	- id_carro (deve ser a chave primária da tabela, além de ser autoincrementada de forma automática)
	- placa (não aceita valores nulos e duplicados)
	- modelo (não aceita valores nulos)
	- tipo (não aceita valores nulos e os tipos de carros cadastrados devem ser: Hatch, Sedan, SUV)

```sql
CREATE TABLE Carro(
	id_carro INT IDENTITTY(1, 1),
	placa VARCHAR(100) NOT NULL,
	modelo VARCHAR(100) NOT NULL,
	tipo VARCHAR(100) NOT NULL,
	CONSTRAINT carro_id_carro_pk PRIMARY KEY(id_carro),
	CONSTRAINT carro_placa_un UNIQUE(placa),
	CONSTRAINT carro_tipo_ck CHECK(tipo IN ('Hatch', 'Sedan', 'SUV'))
)
```

- Tabela 3: Locacoes
	- id_locacao (deve ser a chave primária da tabela, além de ser autoincrementada de forma automática)
	- data_locacao (não aceita valores nulos)
	- data_devolucao (não aceita valores nulos)
	- id_carro (não aceita valores nulos e é uma chave estrangeira)
	- id_cliente (não aceita valores nulos e é uma chave estrangeira)

```sql
CREATE TABLE Locacoes(
	id_locacao INT IDENTITY(1, 1),
	data_locacao VARCHAR(100) NOT NULL,
	data_devolucao VARCHAR(100) NOT NULL,
	id_carro NOT NULL,
	id_cliente NOT NULL,
	CONSTRAINT locacoes_id_locacao_pk PRIMARY KEY(locacoes),
	CONSTRAINT locacoes_id_carro_fk FOREIGN KEY(id_carro) REFERENCES Carro(id_carro),
	CONSTRAINT locacoes_id_cliente_fk FOREIGN KEY(id_cliente) REFERENCES Cliente(id_cliente)
)
```


### Aula 14: Resolução Exercício 2
- Tente violar as constraints criadas para cada tabela. Este exercício é livre. Obs: Para fazer o exercício de violação de constraints basta utilizar o comando INSERT INTO para adicionar valores nas tabelas que não respeitem as restrições (constraints) estabelecidas na criação das tabelas. Ao final, exclua o banco de dados criado.

```sql
INSERT INTO Carro(placa, modelo, tipo)
VALUES
	('ABC-123', 'Hyundai HB20', 'Sedan')
	('ABC-123', 'Fiat Argo', 'Hatch') -- duplicando a placa. Vai conflitar.
	('XZ-123', 'Citroen Cactus', 'Esportivo') -- Check do tipo. Vai conflitar porque é diferente do check.
```


-------------
## Módulo 21: Sequences

### Aula 2: O que é uma Sequence

```sql
-- O que é?
-- Uma sequência (Sequence) é um objeto que utilizamos para criação de números sequenciais automáticos. São usados especialmente para gerar valores sequenciais únicos para as chaves primárias das tabelas.

-- Dessa forma, não precisamos ficar preenchendo a sequência de ids manualmente (como fizemos até então), podemos gerar automaticamente por meio de uma sequence.

/* Sintaxe

CREATE SEQUENCE nome_sequencia
AS tipo
START WITH n
INCREMENT BY n
MAXVALUE n | NO MAXVALUE
MINVALUE n | NO MINVALUE
CYCLE | NO CYCLE;       -- quando atinge o valor máximo, pode ou não voltar do começo

*/
```


### Aula 3: Como criar uma Sequence
- Crie uma sequência para o id_cliente

```sql
CREATE SEQUENCE clientes_seq
AS INT
START WITH 1
INCREMENT BY 1
MAXVALUE 9999999
NO CYCLE

-- Próximo valor da sequência

SELECT NEXT VALUE FOR clientes_seq

-- Excluir uma sequence
DROP SEQUENCE clientes_seq
```


### Aula 4: Como utilizar uma sequence
- Crie uma sequência para o id_projeto

```sql
CREATE SEQUENCE projetos_seq
AS INT
START WITH 1
INCREMENT BY 1
NO MAXVALUE
NO CYCLE

CREATE TABLE dProjetos(
	id_projeto INT,
	nome_projeto VARCHAR(100) NOT NULL,
	CONSTRAINT dprojetos_id_projeto_pk PRIMARY KEY(id_projeto)
)

INSERT INTO dProjeto(id_projeto, nome_projeto)
VALUES
	(NEXT VALUE FOR projetos_seq, 'Planejamento Estratégico'),
	(NEXT VALUE FOR projetos_seq, 'Desenvolvimento de App'),
	(NEXT VALUE FOR projetos_seq, 'Plano de Negócios'),
	(NEXT VALUE FOR projetos_seq, 'Visualização 3D')
```


### Aula 6: Resolução Exercícios 1, 2 e 3
- Crie o Banco de Dados AlugaFacil, onde serão criadas as sequences e tabelas dos exercícios.

```sql
CREATE DATABASE AlufaFacil
USE AlugaFacil
```

- 1. Vamos criar Sequences que serão utilizadas nas tabelas: Carro, Cliente e Locacoes. Essas sequences serão chamadas de: cliente_seq, carro_seq e locaçoes_seq. Todas essas sequences devem começar pelo número 1, incrementar de 1 em 1 e não terem valor máximo.

```sql
CREATE SEQUENCE cliente_seq
AS INT
START WITH 1
INCREMENT BY 1
NO MAXVALUE

CREATE SEQUENCE carro_seq
AS INT
START WITH 1
INCREMENT BY 1
NO MAXVALUE

CREATE SEQUENCE locacoes_seq
AS INT
START WITH 1
INCREMENT BY 1
NO MAXVALUE
```

- 2. Utilize as sequences nas 3 tabelas: Carro, Cliente e Locacoes. Você deve excluir as tabelas existentes e recriá-las. Lembre-se que não é necessário utilizar a constraint IDENTITY nas colunas de chave primária uma vez que nelas serão usadas as Sequences.
- Tabela 1: Cliente
	- id_cliente (deve ser chave primária)
	- nome_cliente (não pode aceitar valores nulos)
	- cnh (não pode aceitar valores nulos e duplicados)
	- cartao (não pode aceitar valores nulos)

```sql
CREATE TABLE Cliente(
	id_cliente INT,
	nome_cliente VARCHAR(100) NOT NULL,
	cnh VARCHAR(100) NOT NULL,
	cartao VARCHAR(100) NOT NULL,
	CONSTRAINT cliente_id_cliente_pk PRIMARY KEY(id_cliente),
	CONSTRATIN cliente_cnh_un UNIQUE(cnh)
)
```

- Tabela 2: Carro
	- id_carro (deve ser a chave primária)
	- placa (não pode aceitar valores nulos e duplicados)
	- modelo (não pode aceitar valores nulos)
	- tipo (não pode aceitar valores nulos. Os tipos de carros cadastrados devem ser: Hatch, Sedan, SUV)

```sql
CREATE TABLE Carro(
	id_carro INT,
	placa VARCHAR(100) NOT NULL,
	modelo VARCHAR(100) NOT NULL,
	tipo VARCHAR(100) NOT NULL,
	CONSTRAINT carro_id_carro_pk PRIMARY KEY(id_carro),
	CONSTRAINT carro_placa_un UNIQUE(placa),
	CONSTRAINT carro_tipo_ck CHECK(tipo IN ('Hatch', 'Sedan', SUV))
)
```

- Tabela 3: Locacoes
	- id_locacao (deve ser a chave primária)
	- data_locacao (não pode aceitar valores nulos)
	- data_devolucao (não pode aceitar valores nulos)
	- id_carro (chave estrangeira)
	- id_cliente (chave estrangeira)

```sql
CREATE TABLE Locacoes(
	id_locacao INT,
	data_locacao VARCHAR(100) NOT NULL,
	data_devolucao VARCHAR(100) NOT NULL,
	id_carro INT,
	id_cliente INT,
	CONSTRAINT locacoes_id_locacao_pk PRIMARY KEY(id_locacao),
	CONSTRAINT locacoes_id_carro_fk FOREIGN KEY(id_carro) REFERENCES Carro(id_carro),
	CONSTRAINT locacoes_id_cliente_fk FOREIGN KEY(id_cliente) REFERENCES Cliente(id_cliente)
)

INSERT INTO Cliente(id_cliente, nome_cliente, cnh, cartao)
VALUES
	(NEXT VALUE FOR cliente_seq, 'Ana', '111111', '111111')
	(NEXT VALUE FOR cliente_seq, 'Bruno', '222222', '222222')
```

- 3. Exclua as sequences criadas.

```sql
DROP SEQUENCE cliente_seq
DROP SEQUENCE carro_seq
DROP SEQUENCE locacoes_seq
```


-------------
## Módulo 22: Transactions

### Aula 2: O que é uma Transaction

```sql
-- 1. O que é uma transaction?
-- Uma transaction é uma ação realizada dentro do banco de dados. Essa ação pode ser uma: atualização, inserção ou exclusão de dados do banco. Precisamos de transações quando estamos alterando o banco de dados de alguma forma, seja inserindo, atualizando ou excluindo dados.

-- Normalmente, não temos muito "controle" sobre transações, a menos que a gente explicite no nosso código que queremos fazer isso. Assim, a ideia de uma transação é agrupar um conjunto de instruções a serem executadas no banco de dados, e ter a flexibilidade de:

-- a. Se algo der errado, desfazer aquela transação
-- b. Se tudo der certo, salvar aquela transação

-- O que podemos fazer com uma transaction?

-- BEGIN TRANSACTION		: iniciá-la
-- ROLLBACK TRANSACTION		: desfazê-la
-- COMMIT			: salvá-la
```


### Aula 3: Iniciando uma Transação, Commit e Rollback
- Iniciando uma transação com COMMIT:

```sql
SELECT * FROM cliente_aux

BEGIN TRANSACTION
INSERT INTO cliente_aux(nome_cliente, genero, data_de_nascimento, cpf)
VALUES
	('Maria Julia', 'F', '30/04/1995', '000.000.000-00')

ROLLBACK TRANSACTION -- Desfez a transação anterior

-- Garantir que não é possível fazer um rollback
INSERT INTO cliente_aux(nome_cliente, genero, data_de_nascimento, cpf)
VALUES
	('Maria Julia', 'F', '30/04/1995', '000.000.000-00')

COMMIT TRANSACTION -- Não consegue desfazer

BEGIN TRANSACTION
UPDATE cliente_aux
SET cpf = '999.999.999-99'
WHERE id_cliente = 1

ROLLBACK TRANSACTION -- Desfez a transação anterior
```


### Aula 4: Criando transações nomeadas

```sql
BEGIN TRANSACTION T1
INSERT INTO cliente_aux(nome_cliente, genero, data_de_nascimento, cpf) VALUES
	('Naldo Reis', 'M', '10/02/1992', '412.889.311-90')

-- Commitando uma transação
COMMT TRANSACTION T1
```


### Aula 5: Commit e Rollback condicionais
- Você deve inserir a cliente Ruth Campos no banco de dados. Se esse nome já existir, desfaça a transação. Se não existir, salve a transação.

```sql
DECLARE @contador INT

BEGIN TRANSACTION T1
INSERT INTO cliente_aux(nome_cliente, genero, data_de_nascimento, cpf)
VALUES
	('Ruth Campos', 'F', '23/03/1992', '111.111.111-11')

SELECT @contador = COUNT(*) FROM cliente_aux WHERE nome_cliente = 'Ruth Campos'

IF @contador = 1
	BEGIN
		COMMIT TRANSACTION T1
		PRINT 'Ruth Campos cadastrada com sucesso.'
	END
ELSE
	BEGIN
		ROLLBACK TRANSACTION T1
		'Ruth Campos já foi cadastrada na tabela. Insert abortado!'
	END
```


### Aula 6 de 9: Transações com tratamento de erros (Try e Catch)

```sql
BEGIN TRY
	BEGIN TRANSACTION T1
	
		UPDATE cliente_aux
		SET data_de_nascimento = '15 de março de 1992'
		WHERE id_cliente = 4
	
	COMMIT TRANSACTION T1 -- Deu um erro, porque está tentando colocar um texto no campo de data.
	PRINT 'Data atualizada com sucesso'
END TRY
BEGIN CATCH
	ROLLBACK TRANSACTION T1
	PRINT 'Data cadastrada inválida'
END CATCH
```

### Aula 7: TRANCOUNT e Transações Aninhadas

```sql
BEGIN TRANSACTION T1
BEGIN TRANSACTION T2

PRINT @@TRANCOUNT -- Conta as transações abertas.

-- Transações aninhadas
BEGIN TRANSACTION T1
	PRINT @@TRANCOUNT
	BEGIN TRANSACTION T2
		PRINT @@TRANCOUNT
	COMMIT TRANSACTION T2
	PRINT @@TRANCOUNT
COMMIT TRANSACTION T1
PRINT @@TRANCOUNT
```


### Aula 9: Resolução Exercícios 1 e 2
- 1. Crie uma tabela chamada Carro com os dados abaixo. Obs: não se preocupe com constraints, pode criar uma tabela simples.
![image](https://github.com/user-attachments/assets/3fca69d0-887e-4446-ab22-cb401d7cf5bb)

```sql
CREATE DATABASE AlugaFacil
USE AlugaFacil

CREATE TABLE Carro(
	id_carro INT,
	placa VARCHAR(100) NOT NULL,
	modelo VARCHAR(100) NOT NULL,
	tipo VARCHAR(100) NOT NULL
)

INSERT INTO Carro(id_carro, placa, modelo, tipo)
VALUES
	(1, 'DAS-1412', 'Hyundai HB20', 'Hatch')
	(2, 'JHG-3902', 'Fiat Cronos', 'Sedan')
	(3, 'IPW-9018', 'Citroen C4 Cactus', 'SUV')
	(4, 'JKR-8891', 'Nissa Kicks', 'SUV')
	(5, 'TRF-5904', 'Chevrolet Onix', 'Sedan')
```

- 2. Execute as seguintes transações no banco de dados, sempre na tabela Carro. Lembre-se de dar um COMMIT para efetivar cada uma das transações.
- a) Inserir uma nova linha com os seguintes valores: id_carro = 6, placa = CDR-0090, modelo = Fiat Argo e tipo = Hatch.

```sql
BEGIN TRANSACTION T1
	INSERT INTO Carro(id_carro, placa, modelo, tipo)
	VALUES
		(6, 'CDR-0090', 'Fiat Argo', 'Hatch')
COMMIT TRANSACTION T1
```

- b) Atualizar o tipo do carro de id = 1 de Hatch para Sedan.

```sql
BEGIN TRANSACTION T2
	UPDATE Carro
	SET tipo = 'Sedan'
	WHERE id_carro = 1
COMMIT TRANSACTION T2
```

- c) Deletar a linha referente ao carro de id = 6.

```sql
BEGIN TRANSACTION T3
	DELETE FROM Carro
	WHERE id_carro = 6
COMMIT TRANSACTION T3
```


-------------
## Módulo 23: Functions

### Aula 2 de 11: O que é uma Function

```sql
-- 1. O que é uma Function?

-- Uma function é um conjunto de comandos que executam ações e retorna um valor escalar. As functions ajudam a simplificar um código. Por exemplo, se você tem um cálculo complexo que aparece diversas vezes no seu código, em vez de repetir várias vezes aquela série de comandos, você pode simplesmente criar uma função e reaproveitá-la sempre que precisar.

-- O próprio SQL tem diversas funções prontas e até agora, já vimos vários exemplos de funções deste tipo, como funções de data, texto, e assim vai.


-- Podemos visualizar as funções do sistema na pasta Programação > Funções > Funções do Sistema
```


### Aula 3: Como criar e utilizar uma Function
- Imagine que você queira fazer uma formatação diferenciada na coluna data_de_nascimento, utilizando a função DATENAME.

```sql
-- Criando uma função para formatação de data usando a DATENAME

CREATE FUNCTION fnDataCompleta(@data AS DATE)
RETURNS VARCHAR(MAX)
AS
BEGIN

	RETURN DATENAME(DW, @Data) + ', ' +
		DATENAME(D, @Data) + ' de ' +
		DATENAME(M, @Data) + ' de ' +
		DATENAME(YY, @Data)

END

SELECT
	nome_cliente,
	data_de_nascimento,
	[dbo].[fnDataCompleta](data_de_nascimento)
FROM
	dCliente
```


### Aula 4: Adicionando uma estrutura condicional em nossa Function

```sql
-- Excluir a function
DROP FUNCTION fnDataCompleta

-- Concatenar a data com o semestre

CREATE OR ALTER FUNCTION fnDataCompleta(@data AS DATE)
RETURNS VARCHAR(MAX)
AS
BEGIN

	RETURN DATENAME(DW, @Data) + ', ' +
		DATENAME(D, @Data) + ' de ' +
		DATENAME(M, @Data) + ' de ' +
		DATENAME(YY, @Data) + ' - ' +
		CASE
			WHEN MONTH(@Data) <= 6 THEN
				'(1º Semestre)'
			ELSE
				'(2º Semestre)'
		END
END
```


### Aula 5 e 6: Criando funções complexas
- Crie uma função para retornar o primeiro nome de cada gerente

```sql
SELECT
	nome_gerente,
	dbo.fnPrimeiroNome(nome_gerente) AS primeiro_nome
FROM dGerente

CREATE OR ALTER FUNCTION fnPrimeiroNome(@nomeCompleto AS VARCHAR(MAX))
RETURNS VARCHAR(MAX)
AS
BEGIN

	DECLARE @posicaoEspaco AS INT
	DECLARE @resposta AS VARCHAR(MAX)

	SET @posicaoEspaco = CHARINDEX(' ', @nomeCompleto)

	IF @posicaoEspaco = 0
		SET @resposta = @nomeCompleto
	ELSE
		SET @resposta = LEFT(@nomeCompleto, CHARINDEX(' ', @nomeCompleto) - 1)
	RETURN @resposta
END 
```


### Aula 8: Resolução Exercício 1
- Crie uma Function que calcule o tempo (em anos) entre duas datas. Essa function deve receber dois argumentos: data_inicial e data_final. Caso a data_final não seja informada, a function deve automaticamente considerar a data atual do sistema. Essa function será usada para calcular o tempo de casa de cada funcionário. Obs: a função DATEDIFF não é suficiente para resolver este problema.

```sql
CREATE OR ALTER FUNCTION CalculaDiferencaDatas(@data_inicial DATE, @data_final DATE)
RETURNS INT
AS
BEGIN
	IF @data_final IS NULL SET @data_final = GETDATE()

	RETURN DATEDIFF(YEAR, @dataInicial, @dataFinal)
END

SELECT
	FirstName,
	HireDate,
	EndDate,
	dbo.CalculaDiferencaDatas(HireDate, EndDate)
FROM DimEmployee
```


### Aula 9: Resolução Exercício 2
- Crie uma function que calcula a bonificação de cada funcionário (5% a mais em relação ao BaseRate). Porém, tome cuidado! Nem todos os funcionários deverão receber bônus...

```sql
CREATE OR ALTER FUNCTION CalculaBonus(@salario FLOAT, @status VARCHAR(100), @percentual FLOAT)
RETURNS FLOAT
AS
BEGIN
	DECLARE @bonus AS FLOAT

	IF @status = 'Current'
		SET @bonus = @salario * @percentual
	ELSE
		SET @bonus = 0

	RETURN @bonus
END

SELECT
	FirstName,
	BaseRate,
	Status,
	dbo.CalculaBonus(BaseRate, Status, 0.5)

```


### Aula 10: Resolução Exercício 3
- Crie uma Function que retorna uma tabela. Esta function deve receber como parâmetro o gênero do cliente e retornar todos os clientes que são do gênero informado na function. Observe que esta function será utilizada particularmente com a tabela DimCustomer

```sql
CREATE OR ALTER FUNCTION select_genero(@genero VARCHAR(100))
RETURNS TABLE
AS
RETURN (SELECT * FROM DimCustomer WHERE gender = @genero)

SELECT * FROM dbo.select_genero('M')
```


### Aula 11: Resolução Exercício 4
- Crie uma Function que retorna uma tabela resumo com o total de produtos por cores. Sua function deve receber 1 argumento, onde será possível especificar de qual marca você deseja o resumo.

```sql
CREATE OR ALTER FUNCTION analisa_cores(@marca VARCHAR(100))
RETURNS TABLE
AS
RETURN (SELECT
		ColorName,
		COUNT(*) Total
	FROM DimProduct
	WHERE BrandName = @marca
	GROUP BY ColorName)

SELECT * FROM dbo.analisa_cores('Contoso')
```


--------------
##  Módulo 24: Procedures

### Aula 2: O que é uma Procedure

```sql
-- 1. O que é uma Procedure
-- É um bloco de código que possui um nome e pode ser armazenado no banco de dados.
-- Ele pode incluir uma série de comandos SQL para executar alguma tarefa.


-- 2. Por que usar uma Procedure
-- Procedures são usadas para fazer tarefas repetitivas que não são possíveis em queries do SQL ou que dariam muito trabalho.
-- Pode incluir estruturas de controle e comandos.

-- 3. Tipos de Procedure
-- Uma Procedure pode ou não aceitar parãmetros de entrada

-- Procedures Com Parâmetros
-- Procedures Sem Parâmetros
```


### Aula 3: Criando uma Procedure Sem Parâmetros
- - Exemplo 1. Crie uma Procedure que executa um SELECT simples (sem parâmetros).

```sql
CREATE PROCEDURE prOrdenaGerentes
AS
BEGIN

	SELECT
		id_gerente,
		nome_gerente,
		salario
	FROM dGerente
	ORDER BY salario DESC

END

EXECUTE prOrdenaGerentes
```


### Aula 4 de 15: Criando uma Procedure Com 1 Parâmetro
- Exemplo 2. Crie uma Procedure que executa um SELECT que recebe um parâmetro de entrada para filtrar a tabela dClientes de acordo com o gênero informado.

```sql
CREATE OR ALTER PROCEDURE prListaClientes(@gen VARCHAR(MAX))
AS
BEGIN
	SELECT
		nome_cliente,
		genero,
		data_de_nascimento,
		cpf
	FROM dCliente
	WHERE genero = @gen
END

EXECUTE prListaClientes 'M'
```


### Aula 5: Criando uma Procedure com mais de 1 parâmetro
- Exemplo 3. Crie uma Procedure que executa um SELECT que recebe um parâmetro de entrada para filtrar a tabela dClientes de acordo com o gênero informado e ano de nascimento informado.

```sql
CREATE OR ALTER PROCEDURE prListaClientes(@gen VARCHAR(MAX), @ano INT)
AS
BEGIN
	SELECT
		nome_cliente,
		genero,
		data_de_nascimento,
		cpf
	FROM dCliente
	WHERE genero = @gen AND YEAR(data_de_nascimento) = @ano
END

EXECUTE prListaClientes 'M', 1989
```


### Aula 6: Criando uma Procedure com Parâmetro Default
- Exemplo 3. Crie uma Procedure que executa um SELECT que recebe um parâmetro de entrada para filtrar a tabela dClientes de acordo com o gênero informado e ano de nascimento informado.

```sql
CREATE OR ALTER PROCEDURE prListaClientes(@gen VARCHAR(MAX) = 'M', @ano INT)
AS
BEGIN
	SELECT
		nome_cliente,
		genero,
		data_de_nascimento,
		cpf
	FROM dCliente
	WHERE genero = @gen AND YEAR(data_de_nascimento) = @ano
END

EXECUTE prListaClientes @ano = 1989
```


### Aula 8: Criando uma Procedure mais Complexa para Cadastro de Contratos - Solução
- Exemplo: Crie uma procedure para cadastrar uma nova assinatura de um contrato na tabela fContratos (com parâmetros).

```sql
-- Gerente: Lucas Sampaio
-- Cliente: Gustavo Barbosa
-- Valor do Contrato: 5000


-- 1º Passo: Definir as variáveis a serem utilizadas.
-- 2º Passo: Armazenar o valor de id_gerente de acordo com o gerente associado
-- 3º Passo: Armazenar o valor de id_cliente de acordo com o nome do cliente
-- 4º Passo: Armazenar a data da assinatura como sendo a data atual do sistema
-- 5º Passo: Utilizar o INSERT INTO para inserir os dados na tabela fContratos

CREATE OR ALTER PROCEDURE prRegistraContrato(@gerente VARCHAR(MAX), @cliente VARCHAR(MAX), @valor FLOAT)
AS
BEGIN

	DECLARE @vIdGerente INT, @vIdCliente INT
	SELECT
		@vIdGerente = id_gerente
	FROM dGerente
	WHERE nome_gerente = @gerente

	SELEC
		@vIdCliente = id_cliente
	FROM dCliente
	WHERE nome_cliente = @cliente

	INSERT INTO fContratos(data_assinatura, id_cliente, id_gerente, valor_contrato)
	VALUES
		(GETDATE(), @vIdCliente, @vIdGerente, @valor)

	PRINT 'Contrato registrado com sucesso!'
END

EXECUTE prRegistraContrato @gerente = 'Lucas Sampario', @cliente = 'Gustavo Barbosa', @valor = 5000
```


### Aula 9: Excluindo uma Procedure

```sql
DROP PROCEDURE prRegistraContrato
```


### Aula 10: Functions vs Procedures

```sql
/*

Temos abaixo uma lista de principais diferenças entre Functions e Procedures.

Diferença 1.
- Procedures são usadas para executar um processo, uma sequência de comandos e blocos SQL.
- Functions são usadas para fazer cálculos

Diferença 2.
- Procedures não podem ser 'chamadas' dentro da cláusula SELECT
- Functions podem ser 'chamadas' dentro da cláusula SELECT (desde que não contenham comandos SELECT)

Diferença 3.
- Procedures não precisam retornar nenhum valor
- Functions precisam retornar algum valor 

*/
```


### Aula 12: Resolução Exercício 1
- Crie uma Procedure que resume o total de produtos por nome da categoria. Essa Procedure deve solicitar ao usuário qual marca deve ser considerada na análise.

```sql
CREATE OR ALTER PROCEDURE analisa_produtos(@marca VARCHAR(100))
AS
BEGIN

	SELECT
		c.ProductCategoryName,
		COUNT(*)
	FROM DimProduct p
	INNER JOIN DimProductSubcategory s ON p.ProductSubcategoryKey = s.ProsuctSubcategoryKey
		INNER JOIN DimProductCategory c ON s.ProductCategoryKey = c.ProductCategoryKey
	WHERE p.BrandName = @marca
	GROUP BY c.ProductCategoryName

END

EXECUTE analisa_produtos @marca = 'Contoso'
```


### Aula 13: Resolução Exercício 2
- Crie uma Procedure que lista os top N clientes de acordo com a data de primeira compra. O valor de N deve ser um parâmetro de entrada da sua Procedure.

```sql
CREATE OR ALTER PROCEDURE lista_top_clientes(@topn INT)
AS
BEGIN

	SELECT TOP(@topn)
		FirstName
		EmailAdress,
		DateFirstPurchase
	FROM DimCustomer
	WHERE CustomerType = 'person'
	ORDER BY DateFirstPurchase

END

EXECUTE lista_top_clientes 100
```


### Aula 14: Resolução Exercício 3
- Crie uma Procedure que recebe 2 argumentos: MÊS (de 1 a 12) e ANO (1996 a 2003). Sua Procedure deve listar todos os funcionários que foram contratados no mês/ano informado.

```sql
CREATE OR ALTER PROCEDURE lista_funcionarios(@mes INT, @ano INT)
AS
BEGIN

	SELECT * FROM DimEmployee
	WHERE DATEPART(MM, HireDate) = @mes AND DATEPAR(YYYY, HireDate) = @ano
	ORDER BY HireDate

END

EXECUTE lista_funcionarios 1, 2000
```


### Aula 15: Resolução Exercícios 4, 5 e 6
- Obs. Para os exercícios 4, 5 e 6, utilize os códigos abaixo.

```sql
DROP DATABASE AlugaFacil
CREATE DATABASE AlugaFacil
USE AlugaFacil

CREATE TABLE Carro(
	id_carro INT,
	placa VARCHAR(100) NOT NULL,
	modelo VARCHAR(100) NOT NULL,
	tipo VARCHAR(100) NOT NULL,
	valor FLOAT NOT NULL,
	CONSTRAINT carro_id_carro_pk PRIMARY KEY(id_carro)
)

INSERT INTO Carro(id_carro, placa, modelo, tipo, valor) VALUES
	(1, 'CRU-1111', 'Chevrolet Cruze', 'Sedan', 140000),
	(2, 'ARG-2222', 'Fiat Argo', 'Hatch', 80000),
	(3, 'COR-3333', 'Toyota Corolla', 'Sedan', 170000),
	(4, 'TIG-4444', 'Caoa Chery Tiggo', 'SUV', 190000)
```

- 4. Crie uma Procedure que insere uma nova linha na tabela Carro. Essa nova linha deve conter os seguintes dados:

```sql
-- id = 5
-- placa = GOL-5555
-- modelo = Volkswagen Gol
-- tipo = Hatch
-- valor = 80000

CREATE OR ALTER PROCEDURE cadastra_carro(@id INT, @placa VARCHAR(100), @modelo VARCHAR(100), @tipo VARCHAR(100), @valor INT)
AS
BEGIN
	BEGIN TRANSACTION
	INSERT INTO Carro(id_carro, placa, modelo, tipo, valor) VALUES
	(@id, @placa, @modelo, @tipo, @valor)

	COMMIT
	PRINT 'Cadastrado com sucesso!'
END

EXECUTE cadastra carro 5, 'GOL-5555', 'Volkswagen Gol', 'Hatch', 80000
```

- 5. Crie uma Procedure que altera o valor de venda de um carro. A Procedure deve receber como parâmetros o id_carro e o novo valor.

```sql
CREATE OR ALTER PROCEDURE atera_valor(@id INT, @novo_valor FLOAT)
AS
BEGIN
	BEGIN TRANSACTION
	UPDATE Carro
	SET valor = @novo_valor
	WHERE id_carro = @id
	COMMIT
END

EXECUTE altera_valor 1, 200000
```

- 6. Crie uma Precedure que exclui um carro a partir do id informado.

```sql
CREATE OR ALTER PROCEDURE delata_carro(@id INT)
AS
BEGIN
	BEGIN TRANSACTION
	DELETE FROM Carro
	WHERE id_carro = @id
	COMMIT
END

EXECUTE deleta_carro 1
```


---------------
##  Módulo 25: Triggers DML 

### Aula 2 de 8: O que é uma Trigger DML

```sql
/* Triggers DML

-- Um Trigger é um gatilho que será disparado automaticamente quando acontecer um evento.

-- Triggers podem ser disparadas por eventos DDL (CREATE, ALTER, DROP) e DML (INSERT, UPDATE, DELETE).


-- Triggers DML

-- 1. Uma Trigger DML é disparada quando um comando INSERT, UPDATE ou DELETE é executado sobre uma tabela ou view.

-- 2. Na hora de criar uma trigger, podemos definir alguns elementos, podemos definir se ela será do tipo AFTER ou INSTEAD OF

*/
```


### Aula 3: Criando uma Trigger DML - AFTER
- Crie uma Trigger que seja disparada APÓS um evento INSERT, UPDATE, DELETE seja executado na tabela dCliente

```sql
CREATE OR ALTER TRIGGER tgClienteAlterado
ON dCliente
AFTER INSERT, UPDATE, DELETE
AS
BEGIN
	PRINT 'Os dados da tabela dCliente foram alterados'
END

INSERT INTO dCliente(nome_cliente, genero, data_de_nascimento, cpf) VALUES
	('Zacarias Neto', 'M', '13/02/1999', '333.333.333-33')

UPDATE dCliente
SET cpf = '130.451.892-10'
WHERE id_cliente = 11

DELETE FROM dCliente
WHERE id_cliente = 11
```


### Aula 4: Tabelas INSERTED e DELETED
- Vamos alterar a trigger anterior para deixá-la mais clara.

```sql
CREATE OR ALTER TRIGGER tgClienteAlterado
ON dCliente
AFTER INSERT, UPDATE, DELETE
AS
BEGIN
	SELECT * FROM INSERTED -- retorna a linha inserida
	SELECT * FROM DELETED -- retorna a linha deletada
END

-- UPDATE acontece um INSERTED e um DELETED
```


### Aula 5: Identificando na Trigger o Evento DML Relacionado


```sql
CREATE OR ALTER TRIGGER tgClienteAlterado
ON dCliente
AFTER INSERT, UPDATE, DELETE
AS
BEGIN
	IF EXISTS (SELECT_ * FROM INSERTED) AND EXISTS (SELECT * FROM DELETED)
		PRINT 'Dados foram atualizados na tabela'
	ELSE IF EXISTS (SELECT * FROM INSERTED)
		PRINT 'Dados foram inseridos na tabela'
	ELSE IF EXISTS (SELECT * FROM DELETED)
		PRINT 'Dados foram excluídos na tabela'
END
```


### Aula 6 e 7: Criando uma Trigger para Controle de Permissão de Cadastro - INSTEAD OF
- Crie uma Trigger que seja disparada sempre EM VEZ de um INSERT, UPDATE e DELETE que for executado na tabela dCliente. O que deve acontecer: se o dia de cadastro for sábado ou domingo, não pode deixar alterar pois está fora do horário comercial.

```sql
SELECT FORMAT(GETDATE(), 'dddd')

CREATE OR ALTER TRIGGER tgControleRegistros
ON dCliente
INSTEAD OF INSERT
AS
BEGIN
	IF FORMAT(GETDATE(), 'dddd') IN ('sábado', 'domingo')
	BEGIN
		RAISERROR('O cadastro de clientes só pode ser feito de segunda à sexta'
		ROLLBACK)
	END
	ELSE
	BEGIN
		INSERT INTO dCliente(nome_cliente, genero, data_de_nascimento, cpf)
		SELECT i.nome_cliente, i.genero,i.data_de_nascimento, i.cpf FROM INSERTED i
	END
END

INSERT INTO dCliente(nome_cliente, genero, data_de_nascimento, cpf) VALUES
	()
```


### 
- Habilitando ou desabilitando uma Trigger DML

```sql
ENABLE TRIGGER tgControleRegistros ON dCliente
```

- Habilitando ou desabilitando todas as Triggers DML de uma tabela

```sql
ENABLLE TREGGER ALL ON dCliente
DISABLE TRIGGER ALL ON dCliente
```

- Excluindo uma Trigger DML

```sql
DROP TRIGGER tgControleRegistros
```


------------
## Módulo 26: Triggers DDL

### Aula 2: O que é uma Trigger DDL

```sql
/* Triggers DDL

-- Um Trigger é um gatilho que será disparado automaticamente quando acontecer um evento.

-- Triggers podem ser disparadas por eventos DDL (CREATE, ALTER, DROP) e DML (INSERT, UPDATE, DELETE).


-- Triggers DDL

-- Uma Trigger DML é disparada quando um comando CREATE, ALTER ou DROP é executado.

*/
```


### Aula 3 de 4: Criando uma Trigger DDL

```sql
CREATE OR ALTER TRIGGER tgRecusarTabelas
ON DATABASE
FOR CREATE_TABLE, ALTER_TABLE, DROP_TABLE
AS
BEGIN
	PRINT 'Não é permitido criação, alteração ou exclusão de tabelas'
	ROLLBACK
END
```


### Aula 4: Habilitando, Desabilitando e Excluindo uma Trigger DDL

```sql
-- Habilitando ou desabilitando uma trigger DDL

DISABLE TRIGGER tgRecusarTabelas ON DATABASE
ENABLE TRIGGER tgRecusarTabelas ON DATABASE

-- Habilitando ou desabilitando todas as triggers DDL de uma tabela

DISABLE TRIGGER ALL ON DATABASE
ENABLE TRIGGER ALL ON DATABASE

-- Excluindo uma trigger DDL

DROP TRIGGER tgRecusarTabelas ON DATABASE
```


--------------
## Módulo 27: Pivot Table

### Aula 2: O que são Pivot Tables

```sql
SELECT
	BrandName,
	COUNT(ProductKey) AS Total_Produtos
FROM
	DimProduct
GROUP BY BrandName


SELECT
	DepartmentName,
	YEAR(HireDate) AS ano.
	COUNT(EmployeeKey) AS Total_Funcionarios
FROM
	DimEmployee
GROUP BY DepartmentName, YEAR(HireDate)
```


### Aula 3: Criando uma Pivot Table

```sql
SELECT
	BrandName,
	COUNT(ProductKey) AS Total_Produtos
FROM
	DimProduct
GROUP BY BrandName

-- 1º) O primeiro passo é selecionar os dados que serão usados como base para criação da Pivot Table

-- 2º) Como não conseguimos aplicar o Pivot diretamente nos dados acima, precisaremos fazer isso indiretamente

-- 3º) Agora sim podemos aplicar o Pivot, incluindo o cálculo desejado e os nomes das colunas a serem consideradas

SELECT * FROM
	(SELECT
		ProductKey,
		BrandName
	FROM
		DimProduct) as Dados
PIVOT(
	COUNT(ProductKey)
	FOR BrandName
	IN ([Northwind Traders]
		,[Contoso]
		,[Tailspin Toys]
		,[Adventure Works]
		,[Southridge Video]
		,[Wide World Importers]
		,[The Phone Company]
		,[Fabrikam]
		,[Litware]
		,[A. Datum]
		,[Proseware]
	)
) AS PivotTable
```


### Aula 4: Adicionando Grupos de Linha à Pivot Table
- Calculando o total de funcionários por departamento

```sql
SELECT
	DepartmentName,
	COUNT(EmployeeKey) Total_Funcionarios
FROM DimEmployee
GROUP BY DepartmentName



SELECT * FROM 
	(SELECT
		EmployeeKey,
		YEAR(HireDate) AS Ano,
		DepartmentName
	FROM DimEmployee) AS Dados
PIVOT(
	COUNT(EmployeeKey)
	FOR DepartmentName
	IN ([Tool Design]
		,[Shipping and Receiving]
		,[Sales]
		,[Research and Development]
		,[Quality Assurance]
		,[Purchasing]
		,[Production]
		,[Production Control]
		,[Marketing]
		,[Information Services]
		,[Human Resources]
		,['Human Resources Contral]
		,[Finance]
		,[Facilities and Maintenance]
		,[Executive]
		,[Engineering]
		,[Document Control])
) AS PivotTable

-- Código para selecionar os DepartmentNames para inserir no IN da PivotTable

SELECT DISTINCT
	',' + QUOTENAME(TRIM(DepartmentName))
FROM DimEmployee
```


### Aula 5: Ordenando Linhas e Colunas de uma Pivot Table

```sql
SELECT * FROM 
	(SELECT
		EmployeeKey,
		YEAR(HireDate) AS Ano,
		DepartmentName
	FROM DimEmployee) AS Dados
PIVOT(
	COUNT(EmployeeKey)
	FOR DepartmentName
	IN ([Document Control]
		, [Engineering]
		, [Executive]
		, [Facilities and Maintenance]
		, [Finance]
		, ['Human Resources Contral]
		, [Human Resources]
		, [Information Services]
		, [Marketing]
		, [Production Control]
		, [Production]
		, [Purchasing]
		, [Quality Assurance]
		, [Research and Development]
		, [Sales]
		, [Shipping and Receiving]
		, [Tool Design])
) AS PivotTable
ORDER BY Ano

-- Código para selecionar os DepartmentNames para inserir no IN da PivotTable em ordem alfabética

SELECT DISTINCT
	',' + QUOTENAME(TRIM(DepartmentName))
FROM DimEmployee
ORDER BY ',' + QUOTENAME(TRIM(DepartmentName))
```


### Aula 6: Adicionando mais linhas aos grupos

```sql
SELECT * FROM 
	(SELECT
		EmployeeKey,
		YEAR(HireDate) AS aAno,
		DATENAME(MM, HireDate) AS Mes
		DepartmentName
	FROM DimEmployee) AS Dados
PIVOT(
	COUNT(EmployeeKey)
	FOR DepartmentName
	IN ([Document Control]
		, [Engineering]
		, [Executive]
		, [Facilities and Maintenance]
		, [Finance]
		, ['Human Resources Contral]
		, [Human Resources]
		, [Information Services]
		, [Marketing]
		, [Production Control]
		, [Production]
		, [Purchasing]
		, [Quality Assurance]
		, [Research and Development]
		, [Sales]
		, [Shipping and Receiving]
		, [Tool Design])
) AS PivotTable
ORDER BY Ano, Mes
```


### Aula 8 e 9: Corrigindo a limitação da Pivot Table de forma dinâmica

```sql
DECLARE @NomeColunas NVARCHAR(MAX) = ''
DECLARE @SQL NVARCHAR(MAX) = ''

SELECT @NomeColunas += QUOTENAME(TRIM(DepartmentName)) + ','
FROM
	(SELECT DISTINCT
		DepartmentName
	FROM DimEmployee) AS Aux

SET @NomeColunas = LEFT(@NomeColunas, LEN(@NomeColunas) - 1)

-- TO IN não aceita a variável. Transformou-se o código em texto e armazenuo-se na variável @SQL

SET @SQL = 
'SELECT * FROM 
	(SELECT
		EmployeeKey,
		YEAR(HireDate) AS aAno,
		DATENAME(MM, HireDate) AS Mes
		DepartmentName
	FROM DimEmployee) AS Dados
PIVOT(
	COUNT(EmployeeKey)
	FOR DepartmentName
	IN (' + @NomeColunas + ')
) AS PivotTable
ORDER BY Ano'

-- Executar uma procedure que transforma a variável @SQL em código e executa.

EXECUTE sp_executesql @SQL
-- 
```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```



