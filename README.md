# Análises em DataBase
Exemplos de análises em Banco de Dados. Select, Order By, Where, Join, Procedures, etc



** -- Exemplo: 1 SELECT * **
SELECT * FROM clientes;
SELECT * FROM pedidos;

-- Exemplo 2: SELECT FROM
SELECT nome, sobrenome, email FROM clientes;

-- Exemplo 3: SELECT AS
SELECT Data_venda AS 'Data da Venda', id_produto AS 'ID do Produto', qtd_vendida AS 'Quantidade Vendida' FROM pedidos;

-- Exemplo 4: SELECT LIMIT
SELECT * FROM pedidos LIMIT 20;

-- ORDER BY
-- Exemplo 1: Faça uma consulta na tabela de clientes e faça uma ordenação 
-- de acordo com o nome do cliente, em ordem alfabética; 

SELECT * 
FROM clientes
ORDER BY nome, sobrenome;

-- Exemplo 2: Faça uma consulta na tabela de clientes e faça uma ordenação 
-- de acordo com a renda anual, da maior para a menor.

SELECT *
FROM clientes
ORDER BY Renda_Anual DESC;

-- Exemplo 3: Faça uma consulta na tabela de clientes e faça uma ordenação
-- de acordo com a data de nascimentos, em ordem do mais novo para o mais velho.

SELECT nome, sobrenome, email, data_nascimento
FROM clientes
ORDER BY Data_Nascimento DESC;

-- WHERE
-- Exemplo 1: Selecione na tabela de clientes apenas os clientes do sexo feminino.
SELECT * FROM clientes
WHERE sexo = 'M';

-- Exemplo 2: Selecione na tabela de produtos apenas os produtos com preço acima de R$2.000

SELECT nome_produto AS 'Nome do produto', preco_unit AS 'Preço do Produto' 
FROM produtos
WHERE Preco_Unit > 2000;

-- Exemplo 3: Selecione os pedidos realizados no dia 10/03/2019.
SELECT * FROM pedidos
WHERE data_venda = '2019-03-10';

-- SUM, COUNT, AVG, MIN e MAX:

-- SUM
SELECT * FROM pedidos; 
SELECT SUM(receita_venda) AS 'Total Venda' FROM pedidos;

-- COUNT
SELECT COUNT(nome) AS 'Qtd Clientes' FROM clientes
WHERE sexo = 'f';

-- AVG
SELECT AVG(Renda_Anual) AS 'Média Renda Anual' FROM clientes; 

-- MIN 
SELECT MIN(preco_unit) AS 'Preço Unitário Mínimo' FROM produtos;

-- MAX 
SELECT MAX(preco_unit) AS 'Preço Unitário Máximo' FROM produtos;

-- GROUP BY
-- Exemplo 1: Crie um agrupamento que mostre a quantidade de produtos por marca.
SELECT * FROM produtos;
SELECT marca_produto, COUNT(marca_produto) AS 'Qtd produtos' 
FROM produtos
GROUP BY marca_produto;

-- Exemplo 2: Crie um agrupamento que mostre a quantidade de clientes por escolaridade.
SELECT * FROM clientes;

SELECT escolaridade, COUNT(escolaridade) AS 'total' FROM clientes
GROUP BY escolaridade;

-- Exemplo 3: Crie um agrupamento que mostre o total de receita (tabela pedidos) por id da loja.
SELECT * FROM pedidos;

SELECT id_loja, SUM(receita_venda) AS 'Total' FROM pedidos
GROUP BY id_loja ORDER BY id_loja ASC;

-- INNER JOIN
-- Exemplo 1: Faça uma consulta à tabela de pedidos que retorne as colunas
-- de Loja, Data_venda e Receita_venda.

