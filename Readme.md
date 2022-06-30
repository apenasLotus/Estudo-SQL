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

BETWEEN retorna os dados entre dois valores/expressões dentre um valor mínimo e um valor máximo.

Ideia: É usado para retornar a intercessão entre dois pontos.
Ex:

        SELECT *
        FROM tabela
        WHERE coluna
        BETWEEN valorMínimo AND valorMáximo

NOT BETWEEN inverte a logica da função, fazendo a mesma retornar tudo fora da intercessão dentre os pontos passados.

### Exemplos/Treino

> Database Teste do Dantas.

        SELECT DISTINCT pro_preco
        FROM produtos
        WHERE pro_preco BETWEEN 5000 AND 10000
        ORDER BY pro_preco ASC

        retorna a intercessão dentre os valore de 5k e 10k

        SELECT DISTINCT pro_preco
        FROM produtos
        WHERE pro_preco NOT BETWEEN 5000 AND 10000
        ORDER BY pro_preco ASC

        retorna tudo oque está fora de 5k e 10k

IN verifica se determinado valor/e ou valores correspondem a outros valores passados na lista.

Ideia: busca no banco de dados e retorna qualquer valor que bater com os parâmeros de pesquisa passados.
Ex:

        valor IN (valor1, valor2...)

        Outro exemplo:
        valor IN (SELECT valor FROM nomeDaTabela)

        Um SELECT dentro de um IN recebe o nome de subSelect ou subQuery, fazendo o mesmo comparar os valores passados apenas com o retorno do SELECT.

### Exemplos/Treino

> Database Teste do Dantas.

        SELECT sgp_cod, pro_descricao
        FROM  produtos
        WHERE  sgp_cod IN (603,602,604)
        ORDER BY sgp_cod ASC

        IMPORTANTE: A verificação da mesma condição acima pode ser feita usando operadores como 'OR', porem a velocidade de execução usando o 'IN' é maior, além de a quantidade de linhas de comando usadas serem menor.

        Comparativo:

        SELECT sgp_cod, pro_descricao
        FROM  produtos
        WHERE  sgp_cod IN (603,602,604)
        ORDER BY sgp_cod ASC

        4 linhas.

        SELECT sgp_cod, pro_descricao
        FROM  produtos
        WHERE  sgp_cod = 603 OR
        sgp_cod = 602 OR
        sgp_cod = 604
        ORDER BY sgp_cod ASC

        6 linhas.


