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

### 

```sql

```

```sql

```








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










