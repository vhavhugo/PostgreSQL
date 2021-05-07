# PostgreSQL

# O que é PostgreSQL? 

É um Sistema Gerenciador de Bancos de Dados (SGBD) relacional que permite armazenar, consultar e manipular dados de inúmeras formas. Dentre seus diversos diferenciais está a linguagem PL/pgSQL  

# O que é PL/pgSQL? 

PL/pgSQL é uma linguagem que possibilita a construção de programas poderosos para empresas que precisam gerenciar tabelas com milhões ou bilhões de registros e, por isso, aprender essa tecnologia facilita o trabalho de quem manipula o SGBD PostgreSQL.  

# Qual a diferença entre SQL e PL/pgSQL?

 Podemos entender a PL/pgSQL como uma extensão da linguagem SQL. Realmente, ela adiciona ao SQL funcionalidades que a tornam uma linguagem de programação completa como controle de fluxo, tratamento de exceções, estruturas de repetições, entre outras.


# Porta utilizada pelo postgreSQL
5432

# Criando tabela

integer = inteiro
real = até 6 digitos
serial = tem icremento automático
numeric = pode definir a qd de casas decimais

varchar(n) = Quando temos mais ou menos o valor do tamanho
char(n) = quando temos o tamanho exato.
text = Não temos idéia do tamanho

boolean = true false null

date = YYYY-MM-DD = 1981-10-02
time = HH24:HI:SS = 17:30:00
timestamp = 1981-10-02 17:30:00

# Criando tabela

CREATE TABLE aluno (
	id SERIAL,
	nome VARCHAR(255),
	cpf CHAR(11),
	observacao TEXT,
	idade INTEGER,
	dinheiro NUMERIC(10,2),
	altura REAL,
	ativo BOOLEAN,
	data_nascimento DATE,
	hora_aula TIME,
	matricula_em TIMESTAMP
	
);

# Inserindo dados na tabela
INSERT INTO aluno (
	nome,
	cpf,
	observacao,
	idade,
	dinheiro,
	altura,
	ativo,
	data_nascimento,
	hora_aula,
	matricula_em
) VALUES (
	'Hugo',
	'12345678901',
	'Lorem Ipsum é simplesmente uma simulação de texto da indústria tipográfica e de impressos, e vem sendo utilizado desde o século XVI',
	39,
	100.50,
	1.01,
	TRUE,
	'1981-10-02',
	'17:30:00',
	'2021-05-06 16:29:05'
);

# Atualizando dados

UPDATE aluno
	SET
	nome = 'Hugo do Valle',
	cpf = 2973895863,
	observacao = 'qbhdhwefilhbelfjbwkelfkejkjefkjwe',
	idade = 35,
	dinheiro = 50.02,
	altura = 1.72,
	ativo = NULL,
	data_nascimento = '1982-10-02',
	hora_aula = '17:00',
	matricula_em = '2021-05-06 17:05:03'
WHERE id = 1;

# Deletando


DELETE FROM aluno WHERE nome = 'Hugo do Valle';

# Pesquisas


SELECT 
	nome AS "Nome do Aluno",
	idade AS "Idade"
	FROM aluno;
	
INSERT INTO aluno (nome) VALUES ('Vinicius Dias');
INSERT INTO aluno (nome) VALUES ('Hugo do Valle');
INSERT INTO aluno (nome) VALUES ('João Roberto');
INSERT INTO aluno (nome) VALUES ('Diogo');
INSERT INTO aluno (nome) VALUES ('Diego');

SELECT *
	FROM aluno
	WHERE nome LIKE '_iego'
	
SELECT *
	FROM aluno
	WHERE nome LIKE 'Di_go'
	
SELECT *
	FROM aluno
	WHERE nome NOT LIKE 'Di_go'
	
SELECT *
	FROM aluno
	WHERE nome LIKE '%i%a%'
// null não existe igual	
SELECT *
	FROM aluno
	WHERE cpf IS NULL
	
SELECT *
	FROM aluno
	WHERE cpf IS NOT NULL
	
SELECT *
	FROM aluno
	WHERE idade BETWEEN 30 AND 30
	
SELECT * FROM aluno WHERE ativo IS NOT NULL

SELECT *
	FROM aluno
	WHERE nome LIKE 'D%'
	AND cpf IS NULL
	
SELECT *
	FROM aluno
	WHERE nome LIKE 'Diogo'
	   OR nome LIKE 'Rodrigo'
	   OR nome LIKE 'Hugo%'