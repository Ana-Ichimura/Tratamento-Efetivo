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
    [atributo]: [descrição da decisão]
    
    EXEMPLO:
    a) Campo endereço: em nosso projeto optamos por um campo multivalorado e composto, pois a empresa 
    pode possuir para cada departamento mais de uma localização... 
    b) justifique!

