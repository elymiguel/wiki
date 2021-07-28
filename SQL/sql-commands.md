## CRIACAO DAS TABELAS

create table livro(
id int,
titulo text,
autor_id int,
editora_id int,
estilo_id int,
sinopse text,
isbn text
);

create table editora(
id int,
nome text,
cidade text,
estado text,
telefone text,
email text
);

create table estilo(
id int,
nome text
);

create table autor(
id int,
nome text,
cidade text,
estado text,
telefone text
);

);

## ALTERAÇÃO DAS TABELAS

alter table esitora rename to editora;


## INSERIR DADOS

insert into editora (id, nome, cidade, estado, telefone, email)
values (1,"SONY","Sao Paulo", "SP", "222 333 444", "sony@sony.com");

insert into editora (id, nome, cidade, estado, telefone, email)
values (2,"MIKE RECORDS","San Francisco", "CA", "420 777 666", "mike@records.com");


insert into autor (id, nome, cidade, estado, telefone)
values (1,"Dan Brown","Los Angeles", "CA", "756 353 345");
insert into autor (id, nome, cidade, estado, telefone)
values (2,"Eckhart Tolle","San Francisco", "CA", "788 667 344");

insert into estilo (id, nome)
values (1,"Suspense");
insert into estilo (id, nome)
values (2,"Drama");
insert into estilo (id, nome)
values (3,"Romance");
insert into estilo (id, nome)
values (4,"Policial");
insert into estilo (id, nome)
values (5,"Ficçao");


insert into livro(id, titulo, autor_id, editora_id, estilo_id, sinopse, isbn)
values(1, "O Poder do Agora", 1, 1, 1, "Find Yourself", "354488699");

insert into livro(id, titulo)
values(2, "Pode Curar Sua Vida");

insert into livro(id, titulo, autor_id, editora_id, estilo_id, sinopse, isbn)
values(3, "Um Vida Leve", 2, 1, 3, "Surfing And Skating", "44556778");

insert into livro(id, titulo, autor_id, editora_id, estilo_id, sinopse, isbn)
values(4, "Estude e Apranda", 1, 1, 4, "Keep Going", "55643121232");



## VISUALIZAR

select nome
from estilo
order by nome;

select nome
from estilo
order by nome desc;

select nome
from editora
where estado="CA";

select nome,cidade,estado
from editora
where estado="CA";

select *
from livro
where id=2;

## DELETAR

delete 
from editora
where id=4;

## UPDATE -- Sempre utilizar WHERE! Caso contrário atualiza todos os registros.

update autor
set telefone="999 999 999";

## ^ NAO UTILIZAR CODIGO ACIMA! CUIDADO ! ^

## UPDATE
update autor
set telefone="755 123 456"
where id=1;

update autor
set telefone="756 455 863"
where id=2;

select * from autor;


update livro
set autor_id=2
where id=1;

select * from livro;


## JOIN

select livro.titulo, autor.nome
from livro, autor
where autor.id = livro.autor_id;

## JOIN Using APELIDO DAS TABELAS --- Livro = l & Autor = a

select l.titulo, a.nome 
from livro l, autor a
where a.id = l.autor_id;

select l.titulo, e.nome
from livro l, editora e
where e.id = l.editora_id;

select l.titulo, a.nome, e.nome
from livro l, autor a, editora e
where a.id = l.autor_id AND e.id = l.editora_id;

## COM RESTRIÇÕES

select l.titulo, a.nome, e.nome, a.telefone
from livro l, autor a, editora e
where a.id = l.autor_id 
AND e.id = l.editora_id
AND a.telefone like "75%";

select l.titulo, e.nome, e.estado
from livro l, editora e
where e.id = l.editora_id 
and e.estado="CA";

select  l.titulo, a.nome, es.nome, ed.nome
from livro l, autor a, editora ed, estilo es
where a.id = l.autor_id
AND ed.id = l.editora_id
AND es.id = l.estilo_id;

