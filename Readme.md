# Treino SQL

**SELECT** é um comando de seleção de todo SQL.

> Ideia: Selecionar uma coluna/+ de uma tabela <br>
> Ex:

```sql

        SELECT coluna1,coluna2...
        FROM tabela.

        SELECT *
        FROM tabela
```

Ou mesmo usando o asterisco '\*', para selecionar toda a tabela.

### Exemplos/Treino

> Database Teste do Dantas.

        Seleciona a tabela completa

```sql

        SELECT * FROM historicos
        SELECT * FROM bairro

        Tabela de clientes
        SELECT * FROM entidades

        Seleciona uma coluna dentro de uma tabela

        SELECT his_texto FROM historicos
        SELECT bairro FROM clientedto
```

Exercício First Name, Last Name.

        Database passada pelo curso. Na teste o nome completo é dado
        em um único campo.

```sql

        SELECT firstName, lastName
        FROM person.person
```

**DISTINCT** é usado para omitir os dados repetidos de uma tabela.

> Ideia: Retornar apenas os dados únicos<br>
> Ex:

```sql

        SELECT DISTINCT coluna1,coluna2...
        FROM tabela
```

### Exemplos/Treino

> Database Teste do Dantas.

```sql

        SELECT DISTINCT ent_nome
        FROM entidades
```

Exercício Sobrenomes únicos na tabela.

        Database passada pelo curso. Na teste o nome completo é dado
        em um único campo.

```sql

        SELECT DISTINCT lastName
        FROM person.Person
```

**WHERE** serve para extrair apenas informações mais 'particulares' da tabela, usando uma verificação para isso.

> Ideia: Realizar uma consulta dentro dos padrões e filtros passados.<br>
> Ex:

```sql

        SELECT coluna1,coluna2...
        FROM tabela
        WHERE condição;
```

        Condições:

                OPERADORES      DESCRIÇÃO

                =               IGUAL
                >               MAIOR QUE
                <               MENOR QUE
                >=              MAIOR IGUAL
                <=              MENOR IGUAL
                <>              DIFERENTE DE
                AND             OPERADOR LÓGICO E
                OR              OPERADOR LÓGICO OU

### Exemplos/Treino

> Database Teste do Dantas.

```sql

        SELECT ent_nome, id_uf
        FROM entidades
        WHERE id_uf = 17 or id_uf = 28
```

        Realizada um filtro em 'nome/id_uf', pegando apenas os id_uf iguais a 17 e 18.
        Dados e nomes referentes ao DataBase teste. Por isso o comentário acima.

```sql

        SELECT com_valor_total
        FROM compras
        WHERE com_valor_total > 5000
        AND com_valor_total < 30000
```

        Realizada um filtro em 'compras', com valor total de 5k até 30k.

### Exemplos/Treino

> Database Teste do Dantas.

        Exercício contem dados diferentes do DataBase usado, logo os parâmetros da pesquisa
        foram alterados, sem mudar a ideia geral do mesmo.

```sql

        SELECT cliente
        FROM clientedto
        WHERE bairro = 'CENTRO'
        AND cidade = 'BARREIRAS'
        AND endereco = 'AVENIDA ACM'
```

        Realizado um filtro na tabela de cliente, retornando apenas o nome dos que moram em 'barreiras', na 'avenida acm' dentro do bairro 'centro'.

Exercício, coletar os produtos com peso dentre 500kg e 700kg.

Exercício 2, retornar os empregados casados e assalariado.

Exercício 3, retornar o email de um usuário para que seja enviada uma cobrança.

        Database passada pelo curso. Logo, nomes de colunas e tabelas diferentes.
        Exercício 1, peso '>500 e <700':

```sql

        SELECT Name
        FROM Production.Product
        WHERE Weight > 500
        AND Weight < 700
```

        Exercício 2, relação de empregados casados e assalariados.

```sql

        SELECT *
        FROM HumanResources.Employee
        WHERE MaritalStatus = 'm'
        AND SalariedFlag = 1
```

        Exercício 3, achar uma pessoa 'X' e retornar seu email de contato.

```sql

        SELECT *
        FROM Person.Person
        WHERE FirstName = 'peter'
        AND LastName = 'krebs'

        SELECT *
        FROM Person.EmailAddress
        WHERE BusinessEntityID = 26
```

        Primeiro foi retornado as informações da pessoa, tais como seu ID
        e após isso foi usado o mesmo para encontrar seu email.

**COUNT** retorna o numero de linhas que bate com a condição que foi definida.

> Ideia: Fazer a contagem de algo, como uma tabela por exemplo.
> Ex:

```sql

        SELECT COUNT(*,coluna1,coluna2...)
        FROM tabela
```

É possível usar o mesmo com outros comandos, DISTINCT por exemplo. Retornando apenas os dados não repetidos do da tabela.

### Exemplos/Treino

> Database Teste do Dantas.

```sql

        SELECT count(*)
        FROM compras

        SELECT count(*)
        FROM marcas

        SELECT count(*)
        FROM produtos
```

Exercício 1, retornar quantos produtos tem cadastrados na tabela de produtos.
Exercício 2, retornar quantos tamanhos de produtos tem cadastrados na tabela de produtos.

        Database passada pelo curso. Logo, nomes de colunas e tabelas diferentes.

        Exercício 1, quantidade de produtos.

```sql

        SELECT count(*)
        FROM Production.Product

        resposta = 504
```

        Exercício 2, tamanho dos produtos.

```sql

        SELECT count(size)
        FROM Production.Product

        resposta = 211
```

**TOP**(**FIRST** no firebird) vai filtrar a quantidade de dados retornados de um SELECT

> Ideia: Limitar os resultados exibidos em 'X' linhas
> Ex:

```sql

        SELECT first 100*
        FROM tabela
```

        Por organização apenas.

```sql

        SELECT *
        FROM  tabela

        FETCH FIRST 100
        ROWS ONLY
```

        Ainda mais completo...

```sql

        SELECT *
        FROM tabela
        ORDER BY ...
        OFFSET (primeiroNumero) ROWS
        FETCH NEXT (ultimoNumero) ROWS ONLY
```

É um comando bem sugestivo, pelo mesmo motivo não irão haver muitos exemplos do mesmo.

**ORDER BY** ordena o retorno do banco de dados a partir de algum 'parâmetro' como data, ordem crescente(asc) ou decrescente(desc)...<hr>
Ideia: Ordenar o retorno da consulta com base em algum parâmetro <br>
Ex:

```sql

        SELECT coluna1,coluna2...
        FROM tabela
        ORDER BY nomeDaColuna parâmetro
```

### Exemplos/Treino

> Database Teste do Dantas.

```sql

        SELECT *
        FROM entidades
        ORDER BY ent_nome, ent_bairro ASC
        OFFSET 0 ROWS
        FETCH NEXT 100 ROWS ONLY
```

        Teste 2

```sql

        SELECT pro_descricao, pro_precO
        FROM produtos
        ORDER BY pro_preco DESC
        OFFSET 0 ROWS
        FETCH NEXT 10 ROWS ONLY
```

Exercício obter os 10 produtos mais caros cadastrados no sistema.

        Database passada pelo curso. Logo, nomes de colunas e tabelas diferentes.

```sql

        SELECT TOP 10 productID
        FROM Production.Product
        ORDER BY listprice DESC
```

**BETWEEN** retorna os dados entre dois valores/expressões dentre um valor mínimo e um valor máximo.

Ideia: É usado para retornar a intercessão entre dois pontos.
Ex:

```sql

        SELECT *
        FROM tabela
        WHERE coluna
        BETWEEN valorMínimo AND valorMáximo
```

**NOT BETWEEN** inverte a logica da função, fazendo a mesma retornar tudo fora da intercessão dentre os pontos passados.

### Exemplos/Treino

> Database Teste do Dantas.

```sql

        SELECT DISTINCT pro_preco
        FROM produtos
        WHERE pro_preco BETWEEN 5000 AND 10000
        ORDER BY pro_preco ASC
```

        retorna a intercessão dentre os valore de 5k e 10k

```sql

        SELECT DISTINCT pro_preco
        FROM produtos
        WHERE pro_preco NOT BETWEEN 5000 AND 10000
        ORDER BY pro_preco ASC
```

        retorna tudo oque está fora de 5k e 10k

**IN** verifica se determinado valor/e ou valores correspondem a outros valores passados na lista.

Ideia: busca no banco de dados e retorna qualquer valor que bater com os parâmeros de pesquisa passados.
Ex:

```sql

        valor IN (valor1, valor2...)

        Outro exemplo:
        valor IN (SELECT valor FROM nomeDaTabela)
```

> Um **SELECT** dentro de um **IN** recebe o nome de subSelect ou subQuery, fazendo o mesmo comparar os valores passados apenas com o retorno do **SELECT**.

### Exemplos/Treino

> Database Teste do Dantas.

```sql

        SELECT sgp_cod, pro_descricao
        FROM  produtos
        WHERE  sgp_cod IN (603,602,604)
        ORDER BY sgp_cod ASC
```

**IMPORTANTE**: A verificação da mesma condição acima pode ser feita usando operadores como 'OR', porem a velocidade de execução usando o 'IN' é maior, além de a quantidade de código usado ser menor.

        Comparativo:

```sql

        SELECT sgp_cod, pro_descricao
        FROM  produtos
        WHERE  sgp_cod IN (603,602,604)
        ORDER BY sgp_cod ASC
```

> 4 linhas.

```sql

        SELECT sgp_cod, pro_descricao
        FROM  produtos
        WHERE  sgp_cod = 603 OR
        sgp_cod = 602 OR
        sgp_cod = 604
        ORDER BY sgp_cod ASC
```

> 6 linhas.

**LIKE** retorna todas as linhas que batem a expressão passada, seja ela uma string completa, ou meso uma condição.

Ideia: retornar todas as linhas da coluna que batem com a/as condições passadas.
Ex:

```sql

        SELECT *
        FROM tabela
        WHERE coluna LIKE 'condição'
```

        Condições:

        OPERADORES      FUNÇÃO
        Tô%             RETORNA OS VALORES QUE COMEÇAM COM 'Tô'
        %Com            RETORNA OS VALORES QUE TERMINAM COM 'Com'
        %FOMEE%         ... COM 'FOMEE' EM QUAISQUER POSIÇÃO
        _BORA%          ... COM 'BORA' EM 2º POSIÇÃO
        COMER_%         ... COM 'COMER' E TENHAM AO MENOS +1 CARÁCTER
        PHP__%          ... COM 'PHP' E TENHAM AO MENOS +2 CARÁCTER
        PRF%V           ... COMEÇAM COM 'PFV' E TERMINAM COM 'V'

                Pfv, leia os exemplos usados...

### Exemplos/Treino

> Database Teste do Dantas.

```sql

        SELECT ent_nome
        FROM  entidades
        WHERE ent_nome LIKE 'GAB%'
        ORDER BY ent_nome ASC
```

```sql

        SELECT DISTINCT pro_preco,pro_descricao
        FROM produtos
        WHERE pro_descricao  LIKE 'N%' AND pro_preco BETWEEN 1500 AND 5000
        ORDER BY pro_descricao ASC
```

> A partir de agora os comandos vão estar de pouco em pouco em linhas únicas.

Exercício, retornar a quantidade de produtos que custam mais de 1,5k no sistema.

```sql

        SELECT COUNT(pro_preco) FROM produtos WHERE pro_preco > 1500
```

Exercício, retornar quantas pessoas começam com a letra 'J' na tabela.

```sql

        SELECT count(ent_nome) FROM ENTIDADES WHERE ent_nome LIKE 'J%'
```

        retornou 41.132 kakka

Exercício, em quantas cidades diferentes os usuários estão cadastrados?

```sql

        SELECT count(DISTINCT ent_cidade) FROM ENTIDADES
```

        retornou 2.057... Banco de dados pequeno né?

Exercício, quantos produtos cadastrados tem 'SMART' no nome.

```sql

        SELECT COUNT(pro_descricao)  FROM produtos WHERE  pro_descricao LIKE '%SMART%'
```

**MIN, MAX, SUM, AVG** são funções que agregam ou combinam dados. Tem um sintaxe bastante didática. Por isso, vão ter poucos exemplos.

Ideia: Agregar ou combinar dados de uma tabela em apenas 1 resultado.
Ex:

```sql

        SELECT SUM(nomeDaColuna)
        FROM tabela
```

Para somar um range especifico, é necessário adicionar uma condição.
Ex:

```sql

        SELECT SUM(nomeDaColuna)
        FROM tabela
        WHERE idTabela < 10
```

Nesse caso, o **SUM** vai calcular os valores dentro do range de ID's menor que 10.<hr>

**SUM** vai somar os valores de retorno, assim como **MIN** retorna o valor mínimo, **MAX** é auto explicativo, e **AVG** retorna a média dos valores.

### Exemplos/Treino

> Database Teste do Dantas.

```sql

        SELECT SUM(COM_VALOR_TOTAL)
        FROM COMPRAS
        WHERE COM_COT_COD < 10
```

> Retornou a soma, com um total de 22,991.41
> Um pouco mais completo:

```sql

        SELECT SUM(COM_VALOR_TOTAL)
        FROM COMPRAS
        WHERE COM_COT_COD BETWEEN 5 AND 15
```

> Retornou a soma da intercessão de 5 e 15. Valor retornado: 88,330.73.

A mesma lógica pode ser aplicada usando os outros comparadores como **MIN**, **MAX** e por aí vai.

**GROUP BY** basicamente divide o resultado da sua pesquisa em grupos, podendo ser aplicada uma função em cada um dos mesmos. Por exemplo:

- Grupo01: calcular a soma da intercessão de 15 até 25.
  -Grupo02 contar o numero de itens do primeiro grupo.

  Ideia: Dividir o resultado da query em grupos distintos, podendo assim executar funções tal como retornar os valores dos mesmo antes da aplicação das funções por exemplo.
  Ex:

```sql

        SELECT coluna1, função(coluna2)
        FROM nomeDaTabela
        GROUP BY coluna1
```

### Exemplos/Treino

> Database Teste do Dantas.

```sql

        SELECT COM_COT_COD ,SUM(COMP_COD)
        FROM COMPRAS
        GROUP BY COM_COT_COD
```

> Traduzindo oque tá acontecendo. 'COM_COT_COD' é o **ID** da compra. 'COMP_COD' é o **CÓDIGO** da compra.<p> Exemplificando com outras tabelas, é a mesma coisa que somar(**SUM**) todas as compras, agrupando(**ORDER BY**) pelo ID do comprador. <p>
> Ou seja, soma todas as compras da pessoa com ID 1,2,3... E agrupa o retorno das mesmas pelo ID.

Outro Ex:

```sql

        SELECT idProduto ,COUNT(idProduto)
        FROM compras
        GROUP BY idProduto
```

> Ele basicamente vai agrupar todos os produtos com ID's iguais, e contar quantas vezes os mesmos se repetem.

> Basicamente vai retornar quantas vezes o 'firstName' aparece, pois o mesmo está sendo agrupado(**GROUP BY**). Ou seja, é juntado todos os nomes iguais, e depois os mesmo são contados.

Outro Ex:

```sql

        SELECT color ,AVG(listPrice)
        FROM product
        GROUP BY color
```

> A query acima, agrupa o retorno pela cor(**GROUP BY**), e pega a media das mesmas pelo preço(**AVG**).<p>
> Ou seja, retorna a média de preço por cor.

Filtrando apenas por uma cor especifica:

```sql

        SELECT color ,AVG(listPrice)
        FROM product
        WHERE color = 'RED'
        GROUP BY color
```

> Basta adicionar a condição dos mesmos.

**HAVING** é usado em conjunto com um **GROUP BY** e funciona como um **WHERE**, mas apenas para os dados agrupados.
Ideia: filtrar os dados retornados de um **GROUP BY**, de forma muito parecida com um **WHERE** mas apenas para os dados agrupados.

```sql

        SELECT coluna1, função(coluna2)
        FROM nomeDaTabela
        GROUP BY coluna1
        HAVING condição
```

> A diferença dentre ambos, é que o **WHERE** aplica os filtros antes dos dados serem agrupados.

Ex:

```sql

        SELECT firstName, COUNT(firstName)
        FROM customers
        GROUP BY firstName
        HAVING COUNT(firstName) > 10
```

> Filtra a query retornando apenas os resultados com ocorrência maior que 10.

### Exemplos/Treino

> Database Teste do Dantas.

Exercício 1, retornar os dados cadastrados mais de 1k de vezes no banco<p>
Exercício 2, retornar os produtos que tem mais vendas da tabela.

        Database passada pelo curso. Logo, nomes de colunas e tabelas diferentes.

        Exercício 1:

```sql


        SELECT ENT_BAIRRO,COUNT(ENT_BAIRRO) o
        FROM ENTIDADES
        GROUP BY ENT_BAIRRO
        ORDER BY o DESC
```

> Seleciona o nome dos bairros cadastrados na tabela de entidades, agrupam as mesmas e conta quantas vezes se repetem.<p> Após isso organiza os resultados utilizando o apelido passado ('**o**') em ordem decrescente.

        Exercício 2:

```sql

        SELECT GRP_COD, SUM(PRO_PRECO) s
        FROM PRODUTOS
        GROUP BY GRP_COD
        ORDER BY s DESC
```

> Retorna os dados por maior valor de soma total, ordenados pelo código dos produtos.

        Retornou os ID's de 1, 708 e 920 como os mais vendidos.

  