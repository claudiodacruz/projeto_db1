# Equipe
- Gustavo Sousa Galisa Albuquerque - mat. 20191370046
- Gabriel Xavier - mat. 20191370025
- Cláudio Cruz - mat. 20191370006

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

Os funcionários possuem um nome, uma matrícula, um email e um telefone profissional. Além disso, a secretária possui registro no Conselho Federal de Arquivologia, enquanto o contador obrigatoriamente é registrado junto ao Conselho de Contabilidade e os advogados possuem OAB própria;

O público alvo desse escritório são pessoas jurídicas (empresas e municípios), mas ele também pode atender a pessoas físicas em demandas específicas;

Os clientes são registrados com nome, CPF ou CNPJ, logradouro completo e telefone (s), que podem ser fixos ou celulares;

Inicialmente, é agendada, com data e hora previamente estabelecida, uma consultoria entre o cliente e um advogado. Caso haja necessidade, o contador poderá auxiliar na elaboração do processo judicial ou parecer;

Durante a consultoria, através de uma pauta específica para cada consulta, será verificada a complexidade do caso e, a partir disso, um contrato é assinado, com um identificador, e um número próprio;

Após a consultoria, poderá ou não surgir um processo. Se surgir, esse processo será de responsabilidade de um ou mais advogados e conterá obrigatoriamente o número do contrato que o fez surgir, um número identificador único gerado pelo sistema da justiça e um número identificador.O processo também estará vinculado a um réu, ao seu defensor e testemunha, além da vara e juiz responsável pela causa ;

O réu é registrado com nome, logradouro completo, telefone e email;

Por sua vez, o réu também possui um advogado constituído (defensor), com nome e OAB, ou é defendido pela defensoria pública;

A testemunha, que possui um id, nome, telefone e email também está ligada ao réu e ao defensor, formando o polo passivo que irá compor o processo;

O processo ainda está vinculado a uma vara, que conterá endereço e número especificador;

Toda vara está diretamente ligada e é coordenada por apenas um juiz de direito, que possui nome e matrícula.

------------

# 2. Modelo conceitual
![](https://github.com/gustavogalisa/projeto_db1/blob/master/projeto_bd_1/modelo_conceitual_definitivo.png)

------------

# 3. Modelo lógico
![](https://github.com/gustavogalisa/projeto_db1/blob/master/pre_projeto_bd1/modelo_completo.png)

------------

# 4. Modelo lógico expandido
![](https://github.com/gustavogalisa/projeto_db1/blob/master/projeto_bd_1/modelo_completo_expandido_definitivo.png)

------------

# 5. Dicionário de dados

# 5. Dicionário de dados

**5.1 Tabela Funcionário**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  idfuncionario |  INT | NÃO  | X  |   | |
| nome  | VARCHAR(45)  | NÃO  |   |   | X|
| telefone  |INT  | NÃO  |   |   | |
| email  | VARCHAR(45)  | NÃO  |   |   | | |

- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idfuncionario |  Chave primária | Identificador do funcionário  | PK_funcionario  | PRIMARY KEY (idfuncionario) |
| nome  | Chave alternativa  | Nome do funcionário  | AK_funcionario  | UNIQUE (nome) | |

**5.2 Tabela Secretária**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  idfuncionario |  INT | NÃO  |   | x  | |
| cfa  | INT  | NÃO  |   |   | x| |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idfuncionario |  Chave primária | Identificador do funcionário | PK_secretaria | PRIMARY KEY (idfuncionario)  |
|  idfuncionario | Chave estrangeira | Chave estrangeira referenciando coluna idfuncionario da tabela funcionario | FK_scretaria_funcionario  |  FOREIGN KEY (idfuncionario) REFERENCES funcionario |
|  cfa |  Chave candidata  | Indica o registro no Conselho Federal de Arquivologia  | AK_secretaria  | UNIQUE (cfa) |

**5.3 Tabela Contador**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  idfuncionario |  INT | NÃO  |   | x  | |
| crc  | INT  | NÃO  |   |   | x | |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idfuncionario |  Chave primária | Identificador do funcionario | PK_contador | PRIMARY KEY (idfuncionario)  |
|  idfuncionario | Chave estrangeira |  Chave estrangeira referenciando coluna idfuncionario da tabela funcionario | FK_contador_funcionario  |  FOREIGN KEY (idfuncionario) REFERENCES funcionario |
|  crc |  Chave candidata  | Indica o registro no Conselho Regional de Contabilidade  | AK_contador  | UNIQUE (crc) |

**5.4 Tabela Advogado**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  idfuncionario |  INT | NÃO  |   | x  | |
| oab  | INT  | NÃO  |   |   |x |
| id_coordena  | INT  | NÃO  |   |  x | | |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idfuncionario |  Chave primária | Identificador do funcionario | PK_advogado | PRIMARY KEY (idfuncionario)  |
|  idfuncionario | Chave estrangeira |  Chave estrangeira referenciando coluna idfuncionario da tabela funcionario |FK_advogado_funcionario	  |  FOREIGN KEY (idfuncionario) REFERENCES funcionario |
|  oab |  Chave candidata  | Indica o registro no Ordem ods Advogados do Brasil  | AK_advogado  | UNIQUE (oab) |
|  id_coordena |  Chave estrangeira | Chave estrangeira referenciando coluna id_coordena da tabela advogado |FK_id_coordenado | FOREIGN KEY (id_coordena) REFERENCES advogado  |

**5.5 Tabela Consulta**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  idconsulta |  INT | NÃO  | X  |   | |
| idfuncionario  | INT  | NÃO  |   | X  | |
| pauta  | VARCHAR(45)  | NÃO  |   |   | | |

- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idconsulta |  Chave primária | Identificador da consulta  | PK_consulta | PRIMARY KEY (idconsulta)  |
| idfuncionario  | Chave estrangeira referenciando coluna idfuncionario da tabela funcionario  | Nome do funcionário  |  FK_consulta_funcionario | FOREIGN KEY (idfuncionario) REFERENCES funcionario |


**5.6 Tabela Agenda**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  hora_inicio |  TIME | NÃO  |   |   | X|
| idcliente | INT  | NÃO  |   |  X |  |
| dia | DATE  | NÃO  |  X |   |  | 
| idconsulta | INT | NÃO  |   |  X |  | |

- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  dia |  Chave primária | Identificador da consulta  | PK_dia | PRIMARY KEY (dia)  |
| idcliente  | Chave estrangeira referenciando coluna idcliente da tabela cliente  | Identificador do cliente  |  FK_agenda_cliente | FOREIGN KEY (idcliente) REFERENCES cliente |
| idconsulta  | Chave estrangeira referenciando coluna idconsulta da tabela consulta  | Identificador da consulta  |  FK_agenda_consulta | FOREIGN KEY (idconsulta) REFERENCES consulta |
| hora_inicio  | Chave candidata  | Indica a hora agendada  | AK_hora_inicio  | UNIQUE (hora_inicio) |

**5.7 Tabela Cliente**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idcliente | INT  | NÃO  |  X |   |  |
| nomeCliente | VARCHAR(45)  | NÃO  |   |   |  |
| rua | VARCHAR(45)  | NÃO  |   |   |  |
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


- Constraints: 

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idcliente |  Chave primária | Identificador do cliente  | PK_cliente_fisico | PRIMARY KEY (idcliente)  |
|  idcliente | Chave estrangeira |  Chave estrangeira referenciando coluna idclienteda tabela cliente | FK_fisico_cliente  |  FOREIGN KEY (idcliente) REFERENCES cliente |
|  cpf |  Chave candidata  | Indica o CPF  | AK_cpf  | UNIQUE (cpf) |
|  cpf |  Check  | Confere se o CPF tem a quantidade correta de números  | CK_cpf  | CHECK		(LEN(cpf) = 11) |

**5.9 Tabela Juridica**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idcliente | INT  | NÃO  |   | X  |  |
| cnpj | INT  | NÃO  |   |   | X |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idcliente |  Chave primária | Identificador do cliente  | PK_cliente_juridico | PRIMARY KEY (idcliente)  |
|  idcliente | Chave estrangeira |  Chave estrangeira referenciando coluna idclienteda tabela cliente | FK_juridica_cleinte  |  FOREIGN KEY (idcliente) REFERENCES cliente |
|  cnpj |  Chave candidata  | Indica o CNPJ  | AK_cnpj  | UNIQUE (cnpj) |
|  cnpj |  Check  | Confere se o CNPJ tem a quantidade correta de números  | CK_cnpj  | CHECK		(LEN(cnpj) = 11) |

**5.10 Tabela Telefone**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| fone | INT  | NÃO  |  X |   |  |
| idcliente | INT  | NÃO  |   |  X |  |
| tipo | VARCHAR(45)  | NÃO  |   |   |  | |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  fone |  Chave primária | Identificador do cliente  | PK_fone | PRIMARY KEY (fone)  |
|  idcliente |  Chave estrangeira referenciando coluna idcliente da tabela cliente | Identificador do cliente  | FK_fone_cliente | FOREIGN KEY (idcliente) REFERENCES cliente  |

**5.11 Tabela Gera**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  idconsulta |  INT | NÃO  |   | X  | |
| idcliente | INT  | NÃO  |   |  X |  |
| dia | DATE  | NÃO  |  X |   |  |
| idcontrato | int  | NÃO  |   |  X |  | |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idconsulta |  Chave estrangeira referenciando coluna idconsulta da tabela consulta | Identificador da consulta  | FK_gera_consulta | FOREIGN KEY (idconsulta) REFERENCES consulta  |
| idcliente  | Chave estrangeira referenciando coluna idcliente da tabela cliente  | Identificador do cliente  |  FK_gera_cliente | FOREIGN KEY (idcliente) REFERENCES cliente |
| dia  | Chave rpimária  | Identificador da data  |  PK_dia | PRIMARY KEY (dia)|
| idcontrato  | Chave estrangeira referenciando coluna contrato da tabela contrato  | Identificador do contrato  |  FK_gera_contrato | FOREIGN KEY (idcontrato) REFERENCES contrato |

**5.12 Tabela Contrato**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idcontrato | INT  | NÃO  |  X |   |  |
| numero_contrato | INT  | NÃO  |   |   | X |
| valor | INT  | NÃO  |   |   | | |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idcontrato |  Chave primária | Identificador do contrato  | PK_contrato | PRIMARY KEY (idcontrato)  |
|  numero_contrato |  Chave candidata | Identificador alternativo do contrato  | AK_contrato | UNIQUE (numero_contrato)  |	

**5.13 Tabela Processo**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  idprocesso |  INT | NÃO  |  X |   | |
| numProcesso | INT  | NÃO  |   |   | X |
|  idcontrato |  INT | NÃO  |   | X  | |
| idedefensor | INT  | NÃO  |   |  X |  |
| idreu | INT  | NÃO  |   |  X |  | 
| idtestemunha | INT  | NÃO  |   |  X |  |
| idvara | INT  | NÃO  |   |  X |  |
| idjuiz | INT  | NÃO  |   |  X | |  |




- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idprocesso |  Chave primária | Identificador do processo  | PK_processo | PRIMARY KEY (idprocesso) |
| idcontrato  | Chave estrangeira referenciando coluna contrato da tabela contrato  | Identificador do contrato  |  FK_processo_contrato | FOREIGN KEY (idcontrato) REFERENCES contrato |
| iddefensor  | Chave estrangeira referenciando coluna iddefensor da tabela defensor  | Identificador do advogado ou representante judicial do réu  |  FK_processo_defensor | FOREIGN KEY (iddefensor) REFERENCES defensor |
| idreu  | Chave estrangeira referenciando coluna idreu da tabela reu  | Identificador do  réu  |  FK_processo_reu | FOREIGN KEY (idreu) REFERENCES reu |
| idtestemunha  | Chave estrangeira referenciando coluna idtestemunha da tabela testemunha  | Identificador da testemunha  |  FK_processo_testemunha | FOREIGN KEY (idtestemunha) REFERENCES testemunha|
| idvara  | Chave estrangeira referenciando coluna idvara da tabela vara  | Identifica a vara ao qual o processo está vinculado  |  FK_processo_vara | FOREIGN KEY (idvara) REFERENCES vara |
| idjuiz  | Chave estrangeira referenciando coluna idjuiz da tabela juiz  | Identifica o juiz ao qual o processo está vinculado  |  FK_processo_juiz | FOREIGN KEY (idjuiz) REFERENCES juiz |
| numProcesso  | Chave candidata  | Identificação única do processo  |  AK_Processo | FUNIQUE		(numProcesso) |
| numProcesso  | Check  | Checa se o número do processo possui a quantidade correta de dígitos  |  CK_numProcesso | CHECK (LEN(numProcesso) = 20)

**5.14 Tabela Vinculado**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idedefensor | int  | NÃO  |   |  X |  |
| idreu | int  | NÃO  |   |  X |  | 
| idtestemunha | int  | NÃO  |   |  X |  | |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
| iddefensor  | Chave estrangeira referenciando coluna iddefensor da tabela defensor  | Identificador do advogado ou representante judicial do réu  |  FK_vinculado_defensor | FOREIGN KEY (iddefensor) REFERENCES defensor |
| idreu  | Chave estrangeira referenciando coluna idreu da tabela reu  | Identificador do  réu  |  FK_vinculado_reu | FOREIGN KEY (idreu) REFERENCES reu |
| idtestemunha  | Chave estrangeira referenciando coluna idtestemunha da tabela testemunha | Identificador da testemunha  |  FK_vinculado_testemunha | FOREIGN KEY (idtestemunha) REFERENCES testemunha |

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

**5.16 Tabela Testemunha**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idtestemunha | INT  | NÃO  |  X |   |  |
| nome | VARCHAR(45)  | NÃO  |   |   | X |
| telefone | INT  | NÃO  |   |   |  |  
| email | INT  | SIM  |   |   |  | |

- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idtestemunha |  Chave primária | Identificador da testemunha  | PK_testemunha | PRIMARY KEY (idtestemunha)  |
|  nome |  Chave candidata | Nome da testemunha  | AK_testemunha | UNIQUE (nome)  |

**5.17 Tabela Juiz**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idjuiz | INT  | NÃO  |  X |   |  |
| nome | VARCHAR(45)  | NÃO  |   |   |  |
| matricula | INT  | NÃO  |   |   |  | |

- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idjuiz |  Chave primária | Identificador do juiz  | PK_juiz | PRIMARY KEY (idjuiz)  |

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
| idjuiz  | Chave estrangeira referenciando coluna idjuiz da tabela juiz  | Identificador do  juiz  |  FK_vara_juiz | FOREIGN KEY (idjuiz) REFERENCES juiz |
| num_vara  | Chave estrangeira referenciando colunanum_vara da tabela vara  | Identificador da vara  |  AK_vara | UNIQUE(num_vara) |
