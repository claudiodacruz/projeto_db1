# Minimundo de um escritório de advocacia

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

# Modelo conceitual
![](https://github.com/gustavogalisa/projeto_db1/blob/master/pre_projeto_bd1/modelo_conceitual.png)

# Modelo lógico
![](https://github.com/gustavogalisa/projeto_db1/blob/master/pre_projeto_bd1/modelo_completo.png)

# Modelo lógico expandido
![](https://github.com/gustavogalisa/projeto_db1/blob/master/pre_projeto_bd1/modelo_completo_expandido.png)

# Dicionário de dados

**Tabela Funcionário**

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

**Tabela Secretária**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  id_func |  INT | NÃO  |   | x  | |
| cfa  | INT  | NÃO  |   |   | | |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | EXPRESSÃO |
| ------------ | ------------ | ------------ | ------------ |
|  idfuncionario |  Chave primária | Chave estrangeira referenciando coluna idfuncionario da tabela funcionario | FOREIGN KEY (idfuncionario) REFERENCES funcionario  |
|  idfuncionario |  Chave primária | Chave primária referenciando coluna idfuncionario da tabela funcionario | PRIMARY KEY (idfuncionario)  |

**Tabela Contador**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  id_func |  INT | NÃO  |   | x  | |
| crc  | INT  | NÃO  |   |   | | |


- Constraints:

| COLUNA |TIPO  | DESCRIÇÃO  | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ |
| idfuncionario |  Chave primária | Chave estrangeira referenciando coluna idfuncionario da tabela funcionario | FOREIGN KEY (idfuncionario) REFERENCES funcionario  |
|  idfuncionario |  Chave primária | Chave primária referenciando coluna idfuncionario da tabela funcionario | PRIMARY KEY (idfuncionario)  |

**Tabela Advogado**

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

**Tabela Consulta**

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

**Tabela Agenda**

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

**Tabela Cliente**

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

**Tabela Fisica**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idcliente | INT  | NÃO  |   | X  |  |
| cpf | INT  | NÃO  |   |   | X |


- Constraints: (**CORRIGIR E ADICIONAR CHECK**)

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idcliente |  Chave primária | Identificador do cliente  | PK_idcliente | PRIMARY KEY (idcliente)  |

**Tabela Juridica**

| ATRIBUTO |TIPO  | NULO  | PK  | FK  | AK |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| idcliente | INT  | NÃO  |   | X  |  |
| cnpj | INT  | NÃO  |   |   | X |


- Constraints: (**CORRIGIR E ADICIONAR CHECK**)

| COLUNA |TIPO  | DESCRIÇÃO  | NOME | EXPRESSÃO
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  idcliente |  Chave primária | Identificador do cliente  | PK_idcliente | PRIMARY KEY (idcliente)  |

**Tabela Telefone**

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
