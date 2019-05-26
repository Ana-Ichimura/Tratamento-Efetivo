# TRABALHO 01: Tratamento Efetivo
Trabalho desenvolvido durante a disciplina de BD1

# Sumário

### 1. COMPONENTES<br>
Integrantes do grupo<br>
Ana Carolina: carolichimura24@gmail.com<br>
Pedro Henrique: phcontas@hotmail.com<br>
Emanuel Medeiros: market_live@outlook.com<br>
Filipe Ribeiro: fillipefs.ribeiro@gmail.com<br>

### 2.INTRODUÇÃO E MOTIVAÇAO<br>
>O sistema "Tratamento Efetivo" é centrado em ofececer meios para melhorar a vida de pessoas que precisam utilizar o sistema de saúde. Apesar dos constantes avanços que a ciência obtem na área da saúde, diversos serviços prestados e oferecidos por hospitais continuam sendo realizados de modo manual.
Baseado na necessidade de automatizar alguns serviços de saúde, o sistema terá como objetivo fornecer dados e informações que auxilie os pacientes a obterem informações de tratamentos e exames que estão sendo realizados ou que foram finalizados. Assim como os pacientes, os médicos poderão visualizar também os tratamentos em que ele faz parte. Para que o sistema funcione de forma adequada é preciso permitir o registro de pacientes, médicos, exames, hospitais, medicamentos e doenças, tais informações são fundamentais para completar os dados de um tratamento que será vinculado no sistema.  O sistema deverá gerar relatórios de modo que mostre informações geradas no sistema de forma didática.

### 3.MINI-MUNDO <br>

> O sistema “Tratamento Efetivo” terá como usuários principais os pacientes e médicos. Será fornecido a esses usuários a possibilidade de registro no sistema. O paciente terá o seu nome, peso, altura, data de nascimento, cpf e endereço registrado no sistema, enquanto do médico será registrado o CRM, nome e especialidade(s). O tramento a ser iniciado terá a sua identificação própria dentro do sistema, e cada tratamento deve conter o paciente especificado, o médico responsável pelo tratamento, a doença a ser tratada, os medicamentos a serem usados, a data de inicio e fim do tratamento e em qual hospital estará ocorrendo o processo. É importante lembrar que o sistema deve tratar o fato do médico ter uma ou mais especialidades (no máximo 3), assim como um tratamento pode ter mais de um medicamento sendo usado nele (no máximo 5). 

### 4.RASCUNHOS BÁSICOS DA INTERFACE (MOCKUPS)<br>

![Arquivo PDF do Protótipo Balsamiq feito para o Sistema Tratamento Efetivo](https://github.com/Ana-Ichimura/Tratamento-Efetivo/blob/master/Telas%20projeto%20BD1%20v2.0.pdf)

#### 4.1 QUAIS PERGUNTAS PODEM SER RESPONDIDAS COM O SISTEMA PROPOSTO?
    
> O Sistema Tratamento Efetivo precisa inicialmente dos seguintes relatórios:
* Relatório que mostre os tratamentos realizados pelo usuário de acordo com o periodo especfiicado por ele. Tal relatório deverá mostrar os tratamentos em andamentos que o paciente está realizando e qual doença está sendo tratada, junto com os médicamentos usados no processo.
* Relatório que informe os respectivos médicos que foram responsáveis por determinados tratamentos, ou seja, será retornada os tratamento que um médico é responsável.
* Relatório que mostre quantos tratamentos está sendo realizado (em andamento) em determinado hospital.
* Relatório que deve estar especificado quais tratamento foram finalizados em determinado hospital.
* Relatório que compara o tempo de duração de cada tratamento de acordo com os registros das etapas no sistema. Com isso a pessoa terá uma noção do tempo gasto em cada tratamento e se for o caso ela poderá otimizar o tempo na próxima vez que for realizar um tratamento parecido.
 
 
#### 4.2 TABELA DE DADOS DO SISTEMA:

https://github.com/Ana-Ichimura/Tratamento-Efetivo/blob/master/Tabela%20de%20dados.xlsx


### 5.MODELO CONCEITUAL<br>
    A) NOTACAO ENTIDADE RELACIONAMENTO 
 
        
![Alt text](https://github.com/Ana-Ichimura/Tratamento-Efetivo/blob/master/Conceitual.jpg)
    
         
    
#### 5.1 Validação do Modelo Conceitual
    Lixeira Inteligente: Jackson William, Lavinia Corteletti, Thiago Moreira,Vinicius Freitas 
    Lista de Compras Online: Matheus Garcias, Letícia Teixeira, Júlia Miranda, Henrique Bastos

#### 5.2 DECISÕES DE PROJETO

    [Tabela TRAMENTO]: [Criação de tabela auxiliar para medicamentos]
    
    a) Campo lista_medicamento: Em vez de criar um campo multivalorado, optamos por criar uma tabela chamada LISTA_MEDICAMENTO que conterá até cinco códigos de medicamentos. Essa lista funcionará como uma tabela auxiliar para a tabela tratamento, já que um tramento pode ter mais de um medicamento sendo usado e por isso vimos a necessidade de criar tal lista.
    
    b) Um campo multivalorado não deixaria as informações legíveis do modo como gostariamos, e mesmo que a criação de uma tabela auxiliar aumente a complexidade do projeto, esse foi um dos únicos meios que encontramos até o momomento de inserior mais de uma informação em um único campo.
    
    [Tabela MEDICO]: [Criação de tabela auxiliar para especialidades]
    
    a) Campo lista_especialidade: Semelhante ao caso citado acima, a tabela LISTA_ESPECIALIDADE contém no máximo três especialidades e foi criada com o intuito de vincular até três tipos de especialidades para um único médico.
    
    b) Prezando pela legibilidade novamente, um campo multivalorado dificultaria a consulta de informações na tabela e a legibilidade delas seria menor.
    
    [Tabela BAIRRO e CIDADE]: [Chave estrangeira para cidade e bairro]
    
    a) Campo cod_estado e cod_cidade: Consultar futuramente a cidade e estado do bairro será mais fácil ao realizar um inner join entre as tabelas ESTADO e CIDADE. Se esses campos não existisse teriamos que fazer uma relação entre quatro tabelas em vez de três. 
    A tabela CIDADE contém o campo cod_estado para facilitar também a consulta de informações no banco de dados, principalmente se for o caso de ver qual o estado de determinadas cidades ou quais cidades pertencem a um determinado estado..
    
    b) Conforme foi dito anteriormente, a consulta para ver a cidade e estado que um bairro pertence torna-se mais simples e ela será indenpendente da tabela endereço, assim como fica mais fácil de saber quais bairros pertecem a um determinado estado ou cidade. 
    Para a tabela cidade é o mesmo caso, a independência da tabela endereço para consultar essas informações torna a consulta mais simples.
    
    [Tabela RUA]: [Chave estrangeira para rua, contendo então o código do bairro,cidade e estado]
    
    a) Campo cod_bairro,cod_cidade e cod_estado: Anteriormente tinhamos optado por colocar o nome da rua diretamente na tabela ENDERECO e o código do bairro, cidade e estado como chave estrangeira na tabela ENDERECO. De modo que simplifique as informações presente na tabela e evite ruas com nomes repetidos, decidimos criar uma tabela chamada RUA e colocar como chave estrangeira o código do bairro, cidade e estado.
    
     b) O número de chaves estrangeiras da tabela ENDERECO será menor, já que usando uma única tabela (RUA) conseguiremos deixar a tabela ENDERECO com três colunas a menos, tendo em vista que as informações relacionadas ao bairro, cidade e estado poderão ser encontradas na tabela rua. Conforme foi dito anteriormente, um dos objetivos é evitar também a repetição do nome da rua na tabela ENDERECO.
     
     
   #### 5.3 DESCRIÇÃO DOS DADOS (Descrição das tabelas e dos campos, das tabelas, considerados de difícil compreensão)
    ESTADO: Tabela que armazena os estados para serem inseridos na tabela endereco, cidade e bairro.
    
    CIDADE: Tabela que armazena os dados das cidades registradas no sistema. Ela terá relação com a tabela enderco e bairro.

    BAIRRO: Tabela que especifica o bairro e em qual estado e cidade o bairro está, já que possui relação com a tabela estado e cidade.

    RUA: Tabela que armazena o nome da rua e o codigo interno do sistema da rua cadastrada. 

    ENDERECO: Tabela que armazena o endereço de um paciente junto com o respectivo código do endereço. Ela terá também a chave estrangeira que especifica a rua desse endereço.
        Campo COD_END: Código do endereço que será usado como chave estrangeira na tabela PACIENTE.
        Campo NUM_RESIDENCIA: Número da casa ou do predio em que o paciente mora.
        Campo NUM_COMPLEMENTO: Caso o paciente more em condomínio, esse campo serve para especificar em qual apartamento o paciente mora.
    
    PACIENTE: Tabela responsável por guardar os dados do paciente.
        COD_PACIENTE: Campo usado como chave primaria para o paciente em vez de colocar o CPF como primary key.
        COD_ENDERECO: Campo para especificar qual é o código do endereço do paciente na tabela endereco.
    
    ESPECIALIDADE: Tabela que contém o registro das especialidades que podem pertencer aos médicos.

    LISTA_ESPECIALIDADE: Será possível registrar para o médico até três especialidades, por isso a tabela lista_especialidade será a responsável por armazenar as possíveis especialidades que o médico venha ter.
        COD_LISTA: Campo que registra um código para ser usado como chave estrangeira na tabela medico, de modo que os médicos tenham uma lista de especialidade.
        PRIM_ESPECIALIDADE/SECU_ESPECIALIDADE/TERC_ESPECIALIDADE: Campos que contém o código de no máximo três especialidades distintas para o médico.

    MEDICO: Tabela para armazenar as informações do médicos, tais como o nome, o crm e sua lista de especialidades.

    MEDICAMENTO: Tabela com o registro dos medicamentos que serão usados nos tratamentos.

    LISTA_MEDICAMENTO: Como pode ser usado mais de um medicamento em um tratamento, a tabela lista_medicamento serve para armazenar até 5 medicamentos onde serão vinculados depois a tabela tratamento através do um código.
        PRIM_COD/SEGU_COD/TERC_COD/QUART_COD/QUINT_COD: Campos que conterá até cinco códigos de medicamentos.
    
    HOSPITAL: Tabela que contém o registro do hospital o qual o tratamento estará sendo realizado.

    DOENCA: Tabela usada para armazenar as doenças a serem tratadas.

    TRATAMENTO: Tabela com as informações de um tramento em andamento ou finalizado. Ela armazena também informações como o paciente que está realizando o tratamento e o hospital o qual o processo está sendo feito.
        LISTA_MEDICAMENTO: Campo com o código da lista de medicamento a serem usados no tratamento.
        NUM_CRM: Campo com o código do CRM do médico.
        INICIO_TRAT e FIM_TRAT: Campo com a respectiva data de inicio e fim do tratamento.

7	MODELO FÍSICO

CREATE TABLE ESTADO(
	COD_ESTADO INT PRIMARY KEY,
	NOME_ESTADO VARCHAR(30)
);


CREATE TABLE CIDADE(
	COD_CIDADE INT PRIMARY KEY,
	NOME_CIDADE VARCHAR(50),
	COD_ESTADO INT,FOREIGN KEY (COD_ESTADO) REFERENCES ESTADO (COD_ESTADO) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE
);


CREATE TABLE BAIRRO(
	COD_BAIRRO INT PRIMARY KEY,
	BAIRRO VARCHAR(50),
	COD_CIDADE INT,
	COD_ESTADO INT, FOREIGN KEY (COD_CIDADE) REFERENCES CIDADE (COD_CIDADE) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (COD_ESTADO) REFERENCES ESTADO (COD_ESTADO) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE
);


CREATE TABLE RUA(
	COD_RUA INT PRIMARY KEY,
	NOME_RUA VARCHAR(50),
	COD_BAIRRO VARCHAR(50),
	COD_CIDADE INT,
	COD_ESTADO INT, FOREIGN KEY (COD_BAIRRO) REFERENCES BAIRRO (COD_BAIRRO) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (COD_CIDADE) REFERENCES CIDADE (COD_CIDADE) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (COD_ESTADO) REFERENCES ESTADO (COD_ESTADO) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE
);


CREATE TABLE ENDERECO(
	COD_END INT PRIMARY KEY, 
	RUA VARCHAR(120),
	CEP INT,
	COD_RUA   INT,
	NUM_RESIDENCIA INT,
	NUM_COMPLEMENTO INT, FOREIGN KEY (COD_RUA) REFERENCES RUA (COD_RUA) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
);

ALTER TABLE ENDERECO DROP COLUMN RUA;

CREATE TABLE PACIENTE(
	COD_PACIENTE INT PRIMARY KEY,
	NOME_PACIENTE VARCHAR(80),
	PESO FLOAT,
	ALTURA FLOAT,
	DATA_NASCIMENTO DATE,
	CPF INT,
	COD_ENDERECO INT, FOREIGN KEY (COD_ENDERECO) REFERENCES ENDERECO (COD_END) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE
);


CREATE TABLE ESPECIALIDADE(
	COD_ESPEC INT PRIMARY KEY,
	NOME_ESPECIALIDADE VARCHAR(30)
);


CREATE TABLE LISTA_ESPECIALIDADE(
	COD_LISTA INT PRIMARY KEY,
	PRIM_ESPECIALIDADE INT,
	SECU_ESPECIALIDADE INT,
	TERC_ESPECIALIDADE INT,
	CRM_MED INT, FOREIGN KEY (PRIM_ESPECIALIDADE) REFERENCES ESPECIALIDADE (COD_ESPEC) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (SECU_ESPECIALIDADE) REFERENCES ESPECIALIDADE (COD_ESPEC) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (TERC_ESPECIALIDADE) REFERENCES ESPECIALIDADE (COD_ESPEC) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
);


CREATE TABLE MEDICO(
	CRM INT PRIMARY KEY,
	NOME_MEDICO VARCHAR(80),
	LISTA_ESPECIALIDADE INT, FOREIGN KEY (LISTA_ESPECIALIDADE) REFERENCES LISTA_ESPECIALIDADE (COD_LISTA) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE
);

ALTER TABLE MEDICO RENAME COLUMN LISTA_ESPECIALIDADE TO COD_LISTPEC;
ALTER TABLE MEDICO ADD UF VARCHAR(2);
ALTER TABLE MEDICO DROP COLUMN UF;
ALTER TABLE MEDICO ADD UF INT;
ALTER TABLE MEDICO ADD CONSTRAINT MEDICO_UF_FKEY FOREIGN KEY (UF) REFERENCES ESTADO (COD_ESTADO) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE;


ALTER TABLE MEDICO RENAME COLUMN LISTA_ESPECIALIDADE TO COD_LISTPEC;

CREATE TABLE DOENCA(
	COD_DOENÇA INT PRIMARY KEY,
	DOENCA VARCHAR(40)
);

ALTER TABLE DOENCA RENAME COLUMN COD_DOENÇA TO COD_DOENCA;

CREATE TABLE HOSPITAIS(
	COD_HOSPITAL INT PRIMARY KEY,
	HOSPITAL VARCHAR(40)
);

ALTER TABLE HOSPITAIS RENAME TO HOSPITAL;

CREATE TABLE MEDICAMENTO(
	COD_MEDICAMENTO INT PRIMARY KEY,
	MEDICAMENTO VARCHAR(40)
);


CREATE TABLE LISTA_MEDICAMENTO(
	COD_LISTA INT PRIMARY KEY,
	PRIM_COD INT,
	SECU_COD INT,
	TERC_COD INT,
	QUART_COD INT,
	QUINT_COD INT, FOREIGN KEY (PRIM_COD) REFERENCES MEDICAMENTO (COD_MEDICAMENTO) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (SECU_COD) REFERENCES MEDICAMENTO (COD_MEDICAMENTO) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (TERC_COD) REFERENCES MEDICAMENTO (COD_MEDICAMENTO) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (QUART_COD) REFERENCES MEDICAMENTO (COD_MEDICAMENTO) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (QUINT_COD) REFERENCES MEDICAMENTO (COD_MEDICAMENTO) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
);


CREATE TABLE TRATAMENTO(
	COD_TRATAMENTO INT PRIMARY KEY,
	COD_PACIENTE INT,
	NUM_CRM INT,
	COD_DOENCA INT,
	COD_LISTMEDICAMENTO INT,
	INICIO_TRAT DATE,
	FIM_TRAT DATE,
	COD_HOSPITAL INT, FOREIGN KEY (COD_PACIENTE) REFERENCES PACIENTE (COD_PACIENTE) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (COD_DOENCA) REFERENCES DOENCA (COD_DOENCA) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (NUM_CRM) REFERENCES MEDICO (CRM_MED) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (COD_LISTMEDICAMENTO) REFERENCES LISTA_MEDICAMENTO (COD_LISTA) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (COD_HOSPITAL) REFERENCES HOSPITAL (COD_HOSPITAL) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE
);

	
ALTER TABLE TRATAMENTO ADD UF_MEDICO VARCHAR(2);
DROP TABLE TRATAMENTO;

CREATE TABLE TRATAMENTO(
	COD_TRATAMENTO INT PRIMARY KEY,
	COD_PACIENTE INT,
	NUM_CRM INT,
	UF_MEDICO INT,
	COD_DOENCA INT,
	COD_LISTMEDICAMENTO INT,
	INICIO_TRAT DATE,
	FIM_TRAT DATE,
	COD_HOSPITAL INT, FOREIGN KEY (COD_PACIENTE) REFERENCES PACIENTE (COD_PACIENTE) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (NUM_CRM) REFERENCES MEDICO (CRM) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (UF_MEDICO) REFERENCES ESTADO (COD_ESTADO) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (COD_DOENCA) REFERENCES DOENCA (COD_DOENCA) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (COD_LISTMEDICAMENTO) REFERENCES LISTA_MEDICAMENTO (COD_LISTA) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (COD_HOSPITAL) REFERENCES HOSPITAL (COD_HOSPITAL) MATCH FULL ON DELETE CASCADE ON UPDATE CASCADE
);


    

