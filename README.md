# banco-de-dados-Mercado-


create table tbl_cliente (
 id int not null primary key auto_increment,
 nome varchar(100) not null,
 cpf varchar(18) not null,
 Rg varchar(15) not null,
 unique index(id)
 
);


create table tbl_email (
id int not null primary key auto_increment,
email varchar(45) not null,
id_cliente int not null,


#Cria Chave estrangeira comunicão entre tabelas#
constraint fk_cliente_email
foreign key (id_cliente)
references tbl_cliente(id),
 unique index(id)
 
);

create table tbl_edereco (
id int not null primary key auto_increment,
Logradouro varchar(60) not null,
bairro varchar(45) not null,
Cep varchar(45) not null,
Cidade varchar(45) not null,
Estado varchar(45) not null,
id_cliente int not null,

constraint fk_tbl_cliente_endereco
foreign key (id_cliente)
references tbl_cliente(id),
unique index(id)

);


create table tbl_vendas (
id int not null primary key auto_increment,
Data_entrega date Not null,
Data_compra date,
valor_pedido float not null,
id_cliente int not null,

constraint  fk_cliente_pedidos
foreign key (id_cliente)
references tbl_cliente(id),
unique index(id) 

);


create table tbl_produtos (
id int not null primary key auto_increment,
nome_produto varchar(50) not null,
descricao text,
valor_compra float not null,
valor_venda float not null,
qtde int not null

);


alter table tbl_produtos
add column id_vendas int,

add constraint fk_venda__produtos
foreign key (id_vendas)
references tbl_vendas(id);


create table tbl_setor (
id int not null primary key auto_increment,
Hortfrut varchar (60),
Panificadora varchar (60),
Acougue varchar (60),
industrializados varchar(60)

);

alter table tbl_produtos
add column id_setor Int,

add constraint fk_setor_produtos
foreign key (id_setor)
references tbl_setor(id);

create table tbl_colaboradores (
id int not null primary key auto_increment,
nome varchar (100) not null,
cargo varchar(50) not null,
id_setor int,

constraint fk_setor_colaborador
foreign key (id_setor)
references tbl_setor(id)
);
