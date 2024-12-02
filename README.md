# SQL SERVER
## Aula 2: CASE WHEN... ELSE (Explicação)
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
