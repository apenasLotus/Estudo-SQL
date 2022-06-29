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

        ELECT DISTINCT ent_nome
        FROM entidades

Exercício Sobrenomes únicos na tabela.

        Database passada pelo curso. Na teste o nome completo é dado
        em um único campo.

        SELECT DISTINCT lastName
        FROM person.Person