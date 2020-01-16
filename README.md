# Equipe
- Gustavo Sousa Galisa Albuquerque - mat. 20191370046
- Gabriel Xavier - mat.
- Cláudio - mat.

------------

# Índice

1. Minimundo
2. Modelo conceitual
3. Modelo lógico
4. Modelo lógico expandido
5. Dicionário de dados
- 5.1 Tabela Funcionário
- 5.2 Tabela Secretária
- 5.3 Tabela Contador
- 5.4 Tabela Advogado
- 5.5 Tabela Consulta
- 5.6 Tabela Agenda
- 5.7 Tabela Cliente
- 5.8 Tabela Física
- 5.9 Tabela Jurídica
- 5.10 Tabela Telefone
- 5.11 Tabela Gera
- 5.12 Tabela Contrato
- 5.13 Tabela Processo
- 5.14 Tabela Vinculado
- 5.15T abela Defensor
- 5.16 Tabela Réu
- 5.17 Tabela Juiz
- 5.18 Tabela Vara

------------
# 1. Minimundo de um escritório de advocacia

Um escritório de advocacia tem três tipos de funcionários: secretária, que também faz a organização dos arquivos e precisa ter conhecimentos de arquivologia, contadores, para realizar perícias contábeis em processos de auditoria, e uma equipe de advogados, que atuam nas áreas civil, trabalhista e administrativa/tributária e são chefiados por um advogado;

Os funcionários possuem um nome, uma matrícula e um telefone profissional. Além disso, a secretária possui registro no Conselho Federal de Arquivologia, enquanto o contador obrigatoriamente é registrado junto ao Conselho de Contabilidade e os advogados possuem OAB própria;

O público alvo desse escritório são pessoas jurídicas (empresas e municípios), mas ele também pode atender a pessoas físicas em demandas específicas;

Os clientes são registrados com nome, CPF ou CNPJ, logradouro completo e telefone (s);

Inicialmente, é agendada, com data e hora previamente estabelecida, uma consultoria entre o cliente e um advogado. Caso haja necessidade, o contador poderá auxiliar na elaboração do processo judicial ou parecer;

Durante a consultoria, através de uma pauta específica para cada consulta, será verificada a complexidade do caso e, a partir disso, um contrato é assinado e o valor é estabelecido;

Após a consultoria, poderá ou não surgir um processo. Se surgir, esse processo será de responsabilidade de um ou mais advogados e conterá obrigatoriamente o nome de pelo menos um advogado, o nome do cliente ao qual está vinculado, um assunto (que pode se repetir), um número identificador único e também estará vinculado a um réu;

O réu pode ser pessoa física ou jurídica e é registrado com nome, logradouro completo, telefone e email;

Por sua vez, o réu também possui um advogado constituído (defensor), com nome e OAB, ou é defendido pela defensoria pública;

O processo ainda está vinculado a uma vara, que conterá endereço e número especificador (1-9);

Toda vara está diretamente ligada e é coordenada por apenas um juiz de direito, que possui nome e matrícula.

------------

# 2. Modelo conceitual
![](https://github.com/gustavogalisa/projeto_db1/blob/master/pre_projeto_bd1/modelo_conceitual.png)

------------

# 3. Modelo lógico
![](https://github.com/gustavogalisa/projeto_db1/blob/master/pre_projeto_bd1/modelo_completo.png)

------------

# 4. Modelo lógico expandido
![](https://github.com/gustavogalisa/projeto_db1/blob/master/pre_projeto_bd1/modelo_completo_expandido.png)

------------

# 5. Dicionário de dados

**5.1 Tabela Funcionário**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  idfuncionario |  INT | NÃO  | X  |   | |
| nome  | VARCHAR(45)  | NÃO  |   |   | X|
| telefone  |INT  | NÃO  |   |   | |
| email  | VARCHAR(45)  | NÃO  |   |   | | |

- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | EXPRESSÃO |
| ------------ | ------------ | ------------ | ------------ |
|  idfuncionario |  Chave primária | Identificador do funcionário  | PRIMARY KEY (idfuncionario)  |
| nome  | Chave alternativa  | Nome do funcionário  |  UNIQUE (nome) |  |

**5.2 Tabela Secretária**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  id_func |  INT | NÃO  |   | x  | |
| cfa  | INT  | NÃO  |   |   | | |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | EXPRESSÃO |
| ------------ | ------------ | ------------ | ------------ |
|  idfuncionario |  Chave primária | Chave estrangeira referenciando coluna idfuncionario da tabela funcionario | FOREIGN KEY (idfuncionario) REFERENCES funcionario  |
|  idfuncionario |  Chave primária | Chave primária referenciando coluna idfuncionario da tabela funcionario | PRIMARY KEY (idfuncionario)  |

**5.3 Tabela Contador**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  id_func |  INT | NÃO  |   | x  | |
| crc  | INT  | NÃO  |   |   | | |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ |
| idfuncionario |  Chave primária | Chave estrangeira referenciando coluna idfuncionario da tabela funcionario | FOREIGN KEY (idfuncionario) REFERENCES funcionario  |
|  idfuncionario |  Chave primária | Chave primária referenciando coluna idfuncionario da tabela funcionario | PRIMARY KEY (idfuncionario)  |

**5.4 Tabela Advogado**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  id_func |  INT | NÃO  |   | x  | |
| oab  | INT  | NÃO  |   |   | |
| id_coordena  | INT  | NÃO  |   |  x | | |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ |
|  idfuncionario |  Chave primária | Chave estrangeira referenciando coluna idfuncionario da tabela funcionario | FOREIGN KEY (idfuncionario) REFERENCES funcionario  |
|  idfuncionario |  Chave primária | Chave primária referenciando coluna idfuncionario da tabela funcionario | PRIMARY KEY (idfuncionario)  |
|  id_coordena |  Chave estrangeira | Chave estrangeira referenciando coluna id_coordena da tabela advogado | FOREIGN KEY (id_coordena) REFERENCES advogado  |

**5.5 Tabela Consulta**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  idconsulta |  INT | NÃO  | X  |   | |
| idfuncionario  | INT  | NÃO  |   | X  | |
| pauta  |INT  | NÃO  |   |   | |
| idcliente | INT  | NÃO  |   |  X |  |
| data | DATE  | NÃO  |   |  X |  | |

- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idconsulta |  Chave primária | Identificador da consulta  | PK_idconsulta | PRIMARY KEY (idconsulta)  |
| idfuncionario  | Chave estrangeira referenciando coluna idfuncionario da tabela funcionario  | Nome do funcionário  |  FK_idfuncionario | FOREIGN KEY (idfuncionario) REFERENCES funcionario |
| idcliente  | Chave estrangeira referenciando coluna idcliente da tabela cliente  | Identificador do cliente  |  FK_idcliente | FOREIGN KEY (idcliente) REFERENCES cliente |
| data  | Chave estrangeira referenciando coluna data da tabela agenda  | Identificador da data  |  FK_data | FOREIGN KEY (data) REFERENCES agenda |

**5.6 Tabela Agenda**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  hora_inicio |  TIME | NÃO  |   |   | X|
| idcliente | INT  | NÃO  |   |  X |  |
| data | DATE  | NÃO  |  X |   |  | |

- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  data |  Chave primária | Identificador da consulta  | PK_data | PRIMARY KEY (data)  |
| idcliente  | Chave estrangeira referenciando coluna idcliente da tabela cliente  | Identificador do cliente  |  FK_idcliente | FOREIGN KEY (idcliente) REFERENCES cliente |
| hora_inicio  | Chave candidata  | Indica a hora agendada  | AK_hora_inicio  | UNIQUE (hora_inicio) |

**5.7 Tabela Cliente**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idcliente | INT  | NÃO  |  X |   |  |
| nomeCliente | VARCHAR(45)  | NÃO  |   |   |  |
| rua | VARCHAR(45)  | NÃO  |   |   |  |
| numero | INT  | NÃO  |   |   |  |
| bairro | VARCHAR(45)  | NÃO  |   |   |  |  |

- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idcliente |  Chave primária | Identificador do cliente  | PK_idcliente | PRIMARY KEY (idcliente)  |

**5.8 Tabela Fisica**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idcliente | INT  | NÃO  |   | X  |  |
| cpf | INT  | NÃO  |   |   | X |


- Constraints: (**CORRIGIR E ADICIONAR CHECK**)

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idcliente |  Chave primária | Identificador do cliente  | PK_idcliente | PRIMARY KEY (idcliente)  |

**5.9 Tabela Juridica**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idcliente | INT  | NÃO  |   | X  |  |
| cnpj | INT  | NÃO  |   |   | X |


- Constraints: (**CORRIGIR E ADICIONAR CHECK**)

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idcliente |  Chave primária | Identificador do cliente  | PK_idcliente | PRIMARY KEY (idcliente)  |

**5.10 Tabela Telefone**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| fone | INT  | NÃO  |  X |   |  |
| idcliente | INT  | NÃO  |   |  X |  |
| tipo | VARCHAR(45)  | NÃO  |   |   |  |


- Constraints: (**CORRIGIR E ADICIONAR CHECK**)

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  fone |  Chave primária | Identificador do cliente  | PK_fone | PRIMARY KEY (fone)  |
|  idcliente |  Chave estrangeira referenciando coluna idcliente da tabela cliente | Identificador do cliente  | PK_fone | FOREIGN KEY (idcliente) REFERENCES cliente  |

**5.11 Tabela Gera**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  idconsulta |  INT | NÃO  |   | X  | |
| idfuncionario  | INT  | NÃO  |   | X  | |
| idcliente | INT  | NÃO  |   |  X |  |
| data | DATE  | NÃO  |   |  X |  |
| idcontrato | int  | NÃO  |   |  X |  | |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idconsulta |  Chave estrangeira referenciando coluna idconsulta da tabela consulta | Identificador da consulta  | FK_idconsulta | FOREIGN KEY (idconsulta) REFERENCES consulta  |
| idfuncionario  | Chave estrangeira referenciando coluna idfuncionario da tabela funcionario  | Nome do funcionário que realizou a consulta  |  FK_idfuncionario | FOREIGN KEY (idfuncionario) REFERENCES funcionario |
| idcliente  | Chave estrangeira referenciando coluna idcliente da tabela cliente  | Identificador do cliente  |  FK_idcliente | FOREIGN KEY (idcliente) REFERENCES cliente |
| data  | Chave estrangeira referenciando coluna data da tabela agenda  | Identificador da data  |  FK_data | FOREIGN KEY (data) REFERENCES agenda |
| idcontrato  | Chave estrangeira referenciando coluna contrato da tabela contrato  | Identificador do contrato  |  FK_idcontrato | FOREIGN KEY (idcontrato) REFERENCES contrato |

**5.12 Tabela Contrato**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idcontrato | INT  | NÃO  |  X |   |  |
| numero_contrato | INT  | NÃO  |   |   | X |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idcontrato |  Chave primária | Identificador do contrato  | PK_idcontrato | PRIMARY KEY (fidcontrato)  |

**5.13 Tabela Processo**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  idprocesso |  INT | NÃO  |  X |   | |
|  idconsulta |  INT | NÃO  |   | X  | |
| idcontrato | int  | NÃO  |   |  X |  |
| data | DATE  | NÃO  |   |  X |  |
| idvara | int  | NÃO  |   |  X |  |
| numProcesso | int  | NÃO  |   |   | X |
| idedefensor | int  | NÃO  |   |  X |  |
| idreu | int  | NÃO  |   |  X |  | |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idprocesso |  Chave primária | Identificador do processo  | PK_idconsulta | PRIMARY KEY (idprocesso) |
|  idconsulta |  Chave estrangeira referenciando coluna idconsulta da tabela consulta | Identificador da consulta  | FK_idconsulta | FOREIGN KEY (idconsulta) REFERENCES consulta  |
| idcontrato  | Chave estrangeira referenciando coluna contrato da tabela contrato  | Identificador do contrato  |  FK_idcontrato | FOREIGN KEY (idcontrato) REFERENCES contrato |
| data  | Chave estrangeira referenciando coluna data da tabela agenda  | Identificador da data  |  FK_data | FOREIGN KEY (data) REFERENCES agenda |
| idvara  | Chave estrangeira referenciando coluna idvara da tabela vara  | Identifica a vara ao qual o processo está vinculado  |  FK_idvara | FOREIGN KEY (idvara) REFERENCES vara |
| iddefensor  | Chave estrangeira referenciando coluna iddefensor da tabela defensor  | Identificador do advogado ou representante judicial do réu  |  FK_iddefensor | FOREIGN KEY (iddefensor) REFERENCES defensor |
| idreu  | Chave estrangeira referenciando coluna idreu da tabela reu  | Identificador do  réu  |  FK_idreu | FOREIGN KEY (idreu) REFERENCES reu |

**5.14 Tabela Vinculado**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idedefensor | int  | NÃO  |   |  X |  |
| idreu | int  | NÃO  |   |  X |  | |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
| iddefensor  | Chave estrangeira referenciando coluna iddefensor da tabela defensor  | Identificador do advogado ou representante judicial do réu  |  FK_iddefensor | FOREIGN KEY (iddefensor) REFERENCES defensor |
| idreu  | Chave estrangeira referenciando coluna idreu da tabela reu  | Identificador do  réu  |  FK_idreu | FOREIGN KEY (idreu) REFERENCES reu |

**5.15 Tabela Defensor**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idedefensor | int  | NÃO  | X  |   |  |
| nome | VARCHAR(45)  | NÃO  |   |   |  |
| oab_def | INT  | NÃO  |   |   | X |
| escritorio | VARCHAR(45)  | NÃO  |   |   |  | |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
| iddefensor  | Chave primária  | Identificador do advogado ou representante judicial do réu  |  PK_iddefensor | PRIMARY KEY (iddefensor)|
| oab_def  | Chave candidata  | Identificador a identificação profissional do advogado que defende o réu  |  AK_oab_def | UNIQUE (oab_def) |

**5.16 Tabela Réu**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idreu | INT  | NÃO  |  X |   |  |
| nome | VARCHAR(45)  | NÃO  |   |   |  |
| cidade | VARCHAR(45)  | NÃO  |   |   |  |
| rua | VARCHAR(45)  | NÃO  |   |   |  |
| email | INT  | NÃO  |   |   |  |
| telefone | INT  | NÃO  |   |   |  |  |

- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idreu |  Chave primária | Identificador do reu  | PK_idreu | PRIMARY KEY (idreu)  |

**5.17 Tabela Juiz**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idjuiz | INT  | NÃO  |  X |   |  |
| nome | VARCHAR(45)  | NÃO  |   |   |  |
| matricula | INT  | NÃO  |   |   |  | |

- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idjuiz |  Chave primária | Identificador do juiz  | PK_idjuiz | PRIMARY KEY (idjuiz)  |

**5.18 Tabela Vara**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idvara | INT  | NÃO  |  X |   |  |
| idjuiz | INT  | NÃO  |   | X  |  |
| num_vara | INT  | NÃO  |   |   | X |
| cidade | VARCHAR(45)  | NÃO  |   |   |  |
| rua | VARCHAR(45)  | NÃO  |   |   |  |
| estado | VARCHAR(45)  | NÃO  |   |   |  | |

- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idvara |  Chave primária | Identificador da vara  | PK_idvara | PRIMARY KEY (idvara)  |
| idjuiz  | Chave estrangeira referenciando coluna idjuiz da tabela juiz  | Identificador do  juiz  |  FK_idjuiz | FOREIGN KEY (idjuiz) REFERENCES juiz |
| num_vara  | Chave estrangeira referenciando colunanum_vara da tabela vara  | Identificador da vara  |  AK_num_vara | UNIQUE(num_vara) |



