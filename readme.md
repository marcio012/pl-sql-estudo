# Estudo de Pl Sql

## Sumário

<!-- TODO: em breve a lista de sumário -->
1. [Início](#inicio)
   1. [Instalação_Docker]
   2. [Comandos]()
   3. [Downloads]()
2. []()

> This is a NOTE

## Inicio<a id="inicio"></a>

Usando docker para criar um container do banco de dados, devido a uso do setup ser um mac, e claro pela praticidade que o docker veio solucionar.

### Instalação do docker

Não entrarei especificamente na instalação pois ja exite uma grande quantidade de tutoriais que abordam isso na grande rede.

__Sites que podem ajuda na instalação e configuração do ambiente:__

### Comandos

Os comandos são faceis de memorizar.

> Os comandos aqui são executados no terminal, no uso do docker.

1. Gerando as credencias do docker:

```bash
$ docker login
```

2. Download da imagem

```bash
$ docker pull store/oracle/database-enterprise:12.2.0.1
```

3. Iniciando uma instancia

```bash
$ docker run -d -it --name <oracle-db> store/oracle/database-enterprise:12.2.0.1
```
4. Conectando ao container
```bash
$ docker exec -it <oracle-db> bash -c "source /home/oracle/.bashrc; sqlplus /nolog"
```
> No comando acima as vezes e necessário digitar o **CONTAINER ID** em vez do **NAMES** do container

**Com o container ativo** iniciaremos as configurações do banco de dados
> os comandos aqui são inseridos no sqlPLus no container do danco

5. Configurando o admin do banco

```sql
connect sys as sysdba;
```

6. Digite o password padrão do container
*'Oradoc_db1'*

7. Altere a sessão

```sql
alter session set "_ORACLE_SCRIPT"=true;
```

8. Crie um novo usuário ou identificação

```sql
create user <identificação> identified by <identificação>;
```

9. Der privilegios ao usuário

```sql
GRANT ALL PRIVILEGES TO <identificação>;
```

### Configuração do SqlDevelop
<!-- TODO: Colocar Imagens  -->

 Username: dummy
 Password: dummy
 Hostname: localhost
 Port: 1521
 Service name: ORCLCDB.localdomain


### Downloads

* [www.docker.com](https://www.docker.com/products/docker-desktop) : Documentação de instalação do docker.
* [docker hub imagem do oracle db](https://hub.docker.com/u/marcioheleno012/content/sub-d9a8495b-e414-450c-a3c0-17ba05c915ce) : Imagem e commandos importante para iniciar a criação do container.
* [Tutorial como configurar o SQL_DEVELOP](https://www.youtube.com/watch?v=ciYsDbBx80s) Aqui um resumo pratico de como configurar o container e a Ide SQL DEVELOP.
* [Download sql develop](https://www.oracle.com/technetwork/pt/developer-tools/sql-developer/downloads/index.html) Download da ferramenta sql_develop
  
## Pl Sql

<!-- TODO: O que é o pl-sql:  -->

## Instuções

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

> [!WARNING]
> O uso do "*" como coringa para retornar todos os campos da tabela.

* **Obs:**

``` sql
SELECT * FROM <tabela>
```

### SQL - instrução select e expressões aritiméticas
---
* **Objetivo Principal**: 
  Realizar cálculos com dados numéricos e datas* obitidas nas consultas SQL utilizando os operadores: **(+) Adição, (-) Subtração, (*) Multiplicação, (/) Divisão**

* **OBS:** Para os cálculos com datas, apenas os operadores de ADIÇÃO e SUBTRAÇÃO são permitidos.

* **Regras de precedencias:**
  
  1. A multiplicação e a divisão ocorrem antes da adição e da subtração;

  2. Se os operadores tiverem a mesma prioridade, eles são avaliados então da esquerda para direita;

  3. Com o uso de parênteses, as regras são sobrepostas.

* Comando:
  
``` sql
SELECT
    l.titulo, l.edicao, l.preco, l.preco+5, l.preco*2, (l.preco+5)*2, l.preco*2
FROM tb_livro l
ORDER BY l.preco;
```

### SQL - instrução select e valores null
---
* **Objetivo Principal**: 
  Dar um valor ausente ou inesistente a um dado, ou tabela.

* **OBS:** Qualquer coluna e tipo de dado pode assumir o valor NULL, desde que não haja restrição:

* **O que é um valor null:**
  
  1. Null é um valor indisponível ou ausencia de valor

  2. É diferente de "em branco"

  3. É diferente de zero

  4. Null e o mesmo que Nulo

  5. O valor null influencia em operações aritméticas

* Comando:
  
  <!-- TODO: Comando Sql com a função null -->
``` sql
SELECT
    l.titulo, l.edicao, l.preco, l.preco+5, l.preco*2, (l.preco+5)*2, l.preco*2
FROM tb_livro l
ORDER BY l.preco;
```

### SQL - instrução select alias 
---
* **Objetivo Principal**: 
  Dixar amigavel e legível os nomes das tabelas

* **OBS:** Qualquer coluna ou tipo de dado pode ter um alias:

* **O que é um alias:**
  
  1. É um nome amigavel de uma determinado campo ou coluna

  2. Serve para facilita a leitura

  3. Pode ser aplicado em procedimento ou calculos

  4. Seu uso e opcional

* Declaração:
  
  - espaço em branco seguido do nome-da-variável ou alias

  ``` sql
  select <nome-da-coluna> nome-do-alias from <nome-da-tabela>;
  ```

  - espaço em branco seguido da palavra resevada **as** podendo

  ``` sql
  select <nome-da-coluna> as nome-do-alias from <nome-da-tabela>;
  ```

* Comando:
  
  <!-- TODO: Comando Sql com a função null -->
``` sql
select l.id_livro, l.titulo, l.edicao, l.id_editora, l.isbn, l.preco, l.qtde_estoque, l.preco * l.qtde_estoque as valorTotal from tb_livro l;
```

### SQL - instrução select operadores de concatenação
---
* **Objetivo Principal**: 
  Unir conteúdo de dois ou mais campos, expressões ou constantes

* Declaração:
  
  Primeiro nome ("Fulano") unir com o Ultimo nome ("De tal"), ao concatenar esses dois conteúdos teremos um novo valor igual a "Fulano De tal"

* Operador "pipe" ou "||"
  O plsql entende que e pra unir a informação que estar na esquerda com a informação que estar a direta

  ``` sql
  select <nome-da-coluna> as nome-do-alias from <nome-da-tabela>;
  ```

* Comando:
  
  <!-- TODO: Comando Sql com a função null -->
``` sql
select l.id_livro, l.titulo, l.edicao, l.id_editora, l.isbn, l.preco, l.qtde_estoque, l.preco * l.qtde_estoque as valorTotal from tb_livro l;
```




### SQL - instrução select uso do Distinct 
---
* **Objetivo Principal**: 
  Dixar amigavel e legível os nomes das tabelas

* **OBS:** Qualquer coluna ou tipo de dado pode ter um alias:

* **O que é um alias:**
  
  1. É um nome amigavel de uma determinado campo ou coluna

  2. Serve para facilita a leitura

  3. Pode ser aplicado em procedimento ou calculos

  4. Seu uso e opcional

* Declaração:
  
  - espaço em branco seguido do nome-da-variável ou alias

  ``` sql
  select <nome-da-coluna> nome-do-alias from <nome-da-tabela>;
  ```

  - espaço em branco seguido da palavra resevada **as** podendo

  ``` sql
  select <nome-da-coluna> as nome-do-alias from <nome-da-tabela>;
  ```

* Comando:
  
  <!-- TODO: Comando Sql com a função null -->
``` sql
select l.id_livro, l.titulo, l.edicao, l.id_editora, l.isbn, l.preco, l.qtde_estoque, l.preco * l.qtde_estoque as valorTotal from tb_livro l;
```

