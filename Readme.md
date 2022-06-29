SELECT é um comando de seleção de todo SQL.

Ideia:  Selecionar uma coluna/+ de uma tabela
Ex: 
        SELECT coluna1,coluna2... 
        FROM tabela.

        SELECT *
        FROM tabela

Ou mesmo usando o asterisco '*', para selecionar toda a tabela.

Exemplos/Treino
Database Teste do Dantas.

        Seleciona a tabela completa
        
        SELECT * FROM historicos
        SELECT * FROM bairro 

        Tabela de clientes
        SELECT * FROM entidades

        Seleciona uma coluna dentro de uma tabela
        
        SELECT his_texto FROM historicos
        SELECT bairro FROM clientedto


Exercício First Name, Last Name.

        Database passada pelo curso. Na teste o nome completo é dado
        em um único campo.

        SELECT firstName, lastName
        FROM person.person

DISTINCT é usado para omitir os dados repetidos de uma tabela.

Ideia: Retornar apenas os dados únicos
Ex:
        SELECT DISTINCT coluna1,coluna2...
        FROM tabela

Exemplos/Treino
Database Teste do Dantas.

        SELECT DISTINCT ent_nome
        FROM entidades

Exercício Sobrenomes únicos na tabela.

        Database passada pelo curso. Na teste o nome completo é dado
        em um único campo.

        SELECT DISTINCT lastName
        FROM person.Person

WHERE serve para extrair apenas informações mais 'particulares' da tabela, usando uma
verificação para isso.

Ideia: Realizar uma consulta dentro dos padrões e filtros passados.
Ex:

        SELECT coluna1,coluna2...
        FROM tabela
        WHERE condição;

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

Exemplos/Treino
Database Teste do Dantas.

        SELECT ent_nome, id_uf 
        FROM entidades 
        WHERE id_uf = 17 or id_uf = 28

        Realizada um filtro em 'nome/id_uf', pegando apenas os id_uf iguais a 17 e 18.
        Dados e nomes referentes ao DataBase teste. Por isso o comentário acima.

        SELECT com_valor_total 
        FROM compras
        WHERE com_valor_total > 5000 
        AND com_valor_total < 30000

        Realizada um filtro em 'compras', com valor total de 5k até 30k.

Exemplos/Treino
Database Teste do Dantas.

        Exercício contem dados diferentes do DataBase usado, logo os parâmetros da pesquisa
        foram alterados, sem mudar a ideia geral do mesmo.

        SELECT cliente 
        FROM clientedto 
        WHERE bairro = 'CENTRO' 
        AND cidade = 'BARREIRAS' 
        AND endereco = 'AVENIDA ACM'

        Realizado um filtro na tabela de cliente, retornando apenas o nome dos que moram em 'barreiras', na 'avenida acm' dentro do bairro 'centro'.

Exercício, coletar os produtos com peso dentre 500kg e 700kg
Exercício 2, retornar os empregados casados e assalariado.

        Database passada pelo curso. Logo, nomes de colunas e tabelas diferentes.

        