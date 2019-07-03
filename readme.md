# Estudo de Pl Sql

## Sumário

<!-- TODO: em breve a lista de sumário -->

## Inicio

Usando docker para criar um container do banco de dados, devido a uso do setup ser um mac, e claro pela praticidade que o docker veio solucionar.

### Instalação do docker

Não entrarei especificamente na instalação pois ja exite uma grande quantidade de tutoriais que abordam isso na grande rede.

__Sites que podem ajuda na instalação e configuração do ambiente:__

* [www.docker.com](https://www.docker.com/products/docker-desktop) : Documentação de instalação do docker.
* [docker hub imagem do oracle db](https://hub.docker.com/u/marcioheleno012/content/sub-d9a8495b-e414-450c-a3c0-17ba05c915ce) : Imagem e commandos importante para iniciar a criação do container.
* [Tutorial como configurar o SQL_DEVELOP](https://www.youtube.com/watch?v=ciYsDbBx80s) Aqui um resumo pratico de como configurar o container e a Ide SQL DEVELOP.
* [Download sql develop](https://www.oracle.com/technetwork/pt/developer-tools/sql-developer/downloads/index.html) Download da ferramenta sql_develop
  
## Pl Sql

<!-- TODO: O que é o pl-sql:  -->

## Instuções:


### SQL - instrução select
---

* **Formato Básico:**
``` sql
SELECT [DISTINCT] <campos> FROM <tabela>
```

* **Definição:**
*Select* : Identifica a coluna a serem exibidas
*From* : Identifica a tabela ou as tabelas que contem aquelas colunas
*DISTINCT* : Opcão para distinguir os valores, retirando duplicidades.

* **Obs:** O uso do "*" como coringa para retornar todos os campos da tabela.



### Comando select.