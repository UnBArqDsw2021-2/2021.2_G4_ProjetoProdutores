<style> #dict th, #dict td { vertical-align: middle; text-align: center; border: 0.5px solid rgba(0,0,0,0.2); } </style>

# Dicionário de Dados

## 1. Versionamento

| Versão | Data       | Descrição               | Autor(es)    |
| ------ | ---------- | ----------------------- | ------------ |
| 1.0    | 17/02/2022 | Abertura do documento   | Thiago       |
| 1.1    | 17/02/2022 | Adição do dicionário geral | Thiago    |
| 1.2    | 17/02/2022 | Adição da descrição das tabelas de entidade | Eduardo e Thiago |
| 1.3    | 17/02/2022 | Adição da descrição das tabelas de relacionamento | Thiago |

## 2. Introdução


## 3. Dicionário de Dados

### 3.1 Descrição Geral das Tabelas de Entidades

<table id="dict">
  <tr>
    <th>Entidade</th>
    <th>Relacionamento</th>
    <th>Nome do Relacionamento</th>
    <th>Descrição</th>
  </tr>
  <tr>
    <td>USUARIO</td>
    <td></td>
    <td></td>
    <td>Cadastro dos dados pessoais dos usuários.</td>
  </tr>
  <tr>
    <td>PRODUTOR</td>
    <td>PROPRIEDADE</td>
    <td>detem</td>
    <td>Cadastro dos dados pessoais de cada produtor</td>
  </tr>
  <tr>
    <td>TECNICO</td>
    <td>PROPRIEDADE</td>
    <td>supervisiona</td>
    <td>Cadastro dos dados dos técnicos.</td>
  </tr>
  <tr>
    <td>CADERNETA_DE_CAMPO</td>
    <td>PLANTIO</td>
    <td>registra</td>
    <td>Cadastro da caderneta de campo que o produtor faz do plantio</td>
  </tr>
  <tr>
    <td rowspan="4">PLANTIO</td>
    <td>CADERNETA_DE_CAMPO</td>
    <td>registra</td>
    <td rowspan="4">Cadastro de uma plantação da propriedade</td>
    <tr>
      <td>CULTURA</td>
      <td>possui</td>
    </tr>
    <tr>
    <td>AGROTOXICO</td>
      <td>contem</td>
    </tr>
    <tr>
      <td>PROPRIEDADE</td>
      <td>pertence</td>
    </tr>
  </tr>
  <tr>
    <td rowspan="3">PROPRIEDADE </td>
    <td>PLANTIO</td>
    <td>pertence</td>
    <td rowspan="3">Cadastro de cada propriedade</td>
    <tr>
      <td>PRODUTOR</td>
      <td>detem</td>
    </tr>
    <tr>
      <td>TECNICO</td>
      <td>supervisiona</td>
    </tr>
  </tr>
  <tr>
    <td rowspan="2">CULTURA</td>
    <td>PLANTIO</td>
    <td>possui</td>
    <td rowspan="2">Cadastro do alimento que está sendo plantado em cada plantio</td>
    <tr>
      <td>AGROTOXICO</td>
      <td>espera</td>
    </tr>
  </tr>
  <tr>
    <td rowspan="3">AGROTOXICO</td>
    <td>PLANTIO</td>
    <td>contem</td>
    <td rowspan="3">Cadastro dos agrotóxicos utilizados nos plantios</td>
    <tr>
      <td>CULTURA</td>
      <td>aplica</td>
      </tr>
    <tr>
      <td>TIPO_AGROTOXICO</td>
      <td>tem</td>
    </tr>
  </tr>
  <tr>
    <td>TIPO_AGROTOXICO</td>
    <td>AGROTOXICO</td>
    <td>tem</td>
    <td>Cadastro dos tipos de agrotóxicos utilizados</td>
  </tr>
</table>
<h6 align = "center">Tabela 1: Descrição Geral das Entidades.</h6>
<h6 align = "center">Fonte: Autores</h6>

### 3.2 Descrição Individual das Tabelas de Entidades

<table id="dict">
  <tr>
    <th colspan="6">USUARIO</th>
  </tr>
  <tr>
    <th>Atributo</th>
    <th>Tipo de Dados</th>
    <th>Tamanho</th>
    <th>Restrições</th>
    <th>Descrição</th>
  </tr>
  <tr>
    <td>idUsuario</td>
    <td>UUID</td>
    <td></td>
    <td>chave primária e obrigatório</td>
    <td>Identificador único do usuário</td>
  </tr>
  <tr>
    <td>cpf</td>
    <td>VARCHAR</td>
    <td>11</td>
    <td>obrigatório e único</td>
    <td>Número do CPF do usuário</td>
  </tr>
  <tr>
    <td>nome</td>
    <td>VARCHAR</td>
    <td>80</td>
    <td>obrigatório</td>
    <td>Nome do usuário</td>
  </tr>
  <tr>
    <td>dataNascimento</td>
    <td>DATE</td>
    <td></td>
    <td>obrigatório</td>
    <td>Data de nascimento do usuário</td>
  </tr>
  <tr>
    <td>senha</td>
    <td>VARCHAR</td>
    <td>255</td>
    <td>obrigatório</td>
    <td>Hash da senha do usuário</td>
  </tr>
  <tr>
    <td>telefone</td>
    <td>VARCHAR</td>
    <td>12</td>
    <td>obrigatório</td>
    <td>Número do telefone do usuário</td>
  </tr>
</table>
<h6 align = "center">Tabela 2: Descrição Individual da tabela USUARIO.</h6>
<h6 align = "center">Fonte: Autores</h6>

<table id="dict">
  <tr>
    <th colspan="6">PRODUTOR</th>
  </tr>
  <tr>
    <th>Atributo</th>
    <th>Tipo de Dados</th>
    <th>Tamanho</th>
    <th>Restrições</th>
    <th>Descrição</th>
  </tr>
  <tr>
    <td>idUsuario</td>
    <td>UUID</td>
    <td></td>
    <td>chave primária, chave estrangeira e obrigatório</td>
    <td>Identificação do usuário</td>
  </tr>
  <tr>
    <td>dap</td>
    <td>VARCHAR</td>
    <td>11</td>
    <td>único e obrigatório</td>
    <td>Declaração de Aptidão ao Pronaf (DAP) do produtor</td>
  </tr>
</table>
<h6 align = "center">Tabela 3: Descrição Individual da tabela PRODUTOR.</h6>
<h6 align = "center">Fonte: Autores</h6>

<table id="dict">
  <tr>
    <th colspan="6">TECNICO</th>
  </tr>
  <tr>
    <th>Atributo</th>
    <th>Tipo de Dados</th>
    <th>Tamanho</th>
    <th>Restrições</th>
    <th>Descrição</th>
  </tr>
  <tr>
    <td>idUsuario</td>
    <td>UUID</td>
    <td></td>
    <td>chave primária, chave estrangeira e obrigatório</td>
    <td>Identificação do usuário</td>
  </tr>
  <tr>
    <td>crea</td>
    <td>VARCHAR</td>
    <td>10</td>
    <td>obrigatório e único</td>
    <td>Número do CREA do técnico</td>
  </tr>
  <tr>
    <td>formacao</td>
    <td>VARCHAR</td>
    <td>80</td>
    <td>obrigatório</td>
    <td>Formação do técnico</td>
  </tr>
  <tr>
    <td>email</td>
    <td>VARCHAR</td>
    <td>120</td>
    <td>obrigatório</td>
    <td>E-mail do técnico</td>
  </tr>
  <tr>
    <td>emailVerificado</td>
    <td>BOOLEAN</td>
    <td></td>
    <td>obrigatório</td>
    <td>Verificar se o e-mail do técnico foi confirmado</td>
  </tr>
</table>
<h6 align = "center">Tabela 4: Descrição Individual da tabela TECNICO.</h6>
<h6 align = "center">Fonte: Autores</h6>

<table id="dict">
  <tr>
    <th colspan="6">PROPRIEDADE</th>
  </tr>
  <tr>
    <th>Atributo</th>
    <th>Tipo de Dados</th>
    <th>Tamanho</th>
    <th>Restrições</th>
    <th>Descrição</th>
  </tr>
  <tr>
    <td>idPropriedade</td>
    <td>INT</td>
    <td></td>
    <td>chave primária e obrigatório</td>
    <td>Identificação da propriedade</td>
  </tr>
  <tr>
    <td>cep</td>
    <td>VARCHAR</td>
    <td>8</td>
    <td>obrigatório</td>
    <td>Número do CEP da propriedade</td>
  </tr>
  <tr>
    <td>estado</td>
    <td>VARCHAR</td>
    <td>2</td>
    <td>obrigatório</td>
    <td>Sigla da unidade federativa em que a propriedade se encontra</td>
  </tr>
  <tr>
    <td>cidade</td>
    <td>VARCHAR</td>
    <td>40</td>
    <td>obrigatório</td>
    <td>Nome da cidade em que a propriedade se encontra</td>
  </tr>
  <tr>
    <td>bairro</td>
    <td>VARCHAR</td>
    <td>40</td>
    <td>obrigatório</td>
    <td>Nome do bairro em que a propriedade se encontra</td>
  </tr>
  <tr>
    <td>logradouro</td>
    <td>VARCHAR</td>
    <td>80</td>
    <td>obrigatório</td>
    <td>Endereço da propriedade</td>
  </tr>
  <tr>
    <td>casa</td>
    <td>INT</td>
    <td></td>
    <td>obrigatório</td>
    <td>Número da propriedade</td>
  </tr>
  <tr>
    <td>complemento</td>
    <td>VARCHAR</td>
    <td>80</td>
    <td>optativo</td>
    <td>Descrição complementar ao endereço</td>
  </tr>
  <tr>
    <td>hectares</td>
    <td>DECIMAL</td>
    <td>6 mais 2 casas decimais</td>
    <td>optativo</td>
    <td>Número de hectares da propriedade</td>
  </tr>
  <tr>
    <td>idProdutor</td>
    <td>UUID</td>
    <td></td>
    <td>chave estrangeira e obrigatório</td>
    <td>Identificador do produtor que detem a propriedade</td>
  </tr>
  <tr>
    <td>idTecnico</td>
    <td>UUID</td>
    <td></td>
    <td>chave estrangeira e obrigatório</td>
    <td>Identificador do técnico que supervisiona a propriedade</td>
  </tr>
</table>
<h6 align = "center">Tabela 5: Descrição Individual da tabela PROPRIEDADE.</h6>
<h6 align = "center">Fonte: Autores</h6>

<table id="dict">
  <tr>
    <th colspan="6">PLANTIO</th>
  <tr>
  <tr>
    <th>Atributo</th>
    <th>Tipo de Dados</th>
    <th>Tamanho</th>
    <th>Restrições</th>
    <th>Descrição</th>
  </tr>
  <tr>
    <td>idPlantio</td>
    <td>INT</td>
    <td></td>
    <td>chave primária e obrigatório</td>
    <td>Identificação do plantio</td>
  <tr>
  </tr>
    <td>dataPlantio</td>
    <td>DATE</td>
    <td></td>
    <td>obrigatório</td>
    <td>Data em que o produtor plantou a cultura</td>
  </tr>
  <tr>
    <td>numeroTalhao</td>
    <td>INT</td>
    <td></td>
    <td>obrigatório</td>
    <td>Número do talhão que o produtor plantou</td>
  </tr>
  <tr>
    <td>idCultura</td>
    <td>INT</td>
    <td></td>
    <td>chave estrangeira e obrigatório</td>
    <td>Identificação da cultura que foi plantada</td>
  </tr>
  <tr>
    <td>idPropriedade</td>
    <td>INT</td>
    <td></td>
    <td>chave estrangeira e obrigatório</td>
    <td>Identificação da propriedade</td>
  </tr>
  <tr>
    <td>estado</td>
    <td>CHAR</td>
    <td>1</td>
    <td>obrigatório</td>
    <td>Estado atual do plantio. Podendo ser Plantado, PeriodoDeCarencia, Colheita, Finalizado e etc</td>
  </tr>
</table>
<h6 align = "center">Tabela 6: Descrição Individual da tabela PLANTIO.</h6>
<h6 align = "center">Fonte: Autores</h6>

<table id="dict">
  <tr>
    <th colspan="6">CADERNETA_DE_CAMPO</th>
  </tr>
  <tr>
    <th>Atributo</th>
    <th>Tipo de Dados</th>
    <th>Tamanho</th>
    <th>Restrições</th>
    <th>Descrição</th>
  </tr>
  <tr>
    <td>numeroSerie</td>
    <td>VARCHAR</td>
    <td>11</td>
    <td>chave primária e obrigatório</td>
    <td>Número de identificação da caderneta do produtor</td>
  </tr>
  <tr>
    <td>dataColheita</td>
    <td>DATE</td>
    <td></td>
    <td>único e obrigatório</td>
    <td>Data em que o produtor colheu o plantio</td>
  </tr>
  <tr>
    <td>idPlantio</td>
    <td>INT</td>
    <td></td>
    <td>chave estrangeira, único e obrigatório</td>
    <td>Identificação do plantio</td>
  </tr>
</table>
<h6 align = "center">Tabela 7: Descrição Individual da tabela CADERNETA_DE_CAMPO.</h6>
<h6 align = "center">Fonte: Autores</h6>



<table id="dict">
  <tr>
    <th colspan="6">CULTURA</th>
  </tr>
  <tr>
    <th>Atributo</th>
    <th>Tipo de Dados</th>
    <th>Tamanho</th>
    <th>Restrições</th>
    <th>Descrição</th>
  </tr>
  <tr>
    <td>idCultura</td>
    <td>INT</td>
    <td></td>
    <td>chave primária e obrigatório</td>
    <td>Número de identificação da cultura</td>
  </tr>
  <tr>
    <td>nome</td>
    <td>VARCHAR</td>
    <td>30</td>
    <td>obrigatório</td>
    <td>Nome da cultura</td>
  </tr>
</table>
<h6 align = "center">Tabela 8: Descrição Individual da tabela CULTURA.</h6>
<h6 align = "center">Fonte: Autores</h6>

<table id="dict">
  <tr>
    <th colspan="6">AGROTOXICO</th>
  </tr>
  <tr>
    <th>Atributo</th>
    <th>Tipo de Dados</th>
    <th>Tamanho</th>
    <th>Restrições</th>
    <th>Descrição</th>
  </tr>
  <tr>
    <td>idAgrotoxico</td>
    <td>INT</td>
    <td></td>
    <td>chave primária e obrigatório</td>
    <td>Número de identificação do agrotóxico</td>
  </tr>
  <tr>
    <td>nome</td>
    <td>VARCHAR</td>
    <td>40</td>
    <td>obrigatório</td>
    <td>Nome do agrotóxico</td>
  </tr>
  <tr>
    <td>idTipoAgrotoxico</td>
    <td>INT</td>
    <td></td>
    <td>chave estrangeira e obrigatório</td>
    <td>Número de identificação do tipo do agrotóxico</td>
  </tr>
</table>
<h6 align = "center">Tabela 9: Descrição Individual da tabela AGROTOXICO.</h6>
<h6 align = "center">Fonte: Autores</h6>

<table id="dict">
  <tr>
    <th colspan="6">TIPO_AGROTOXICO</th>
  </tr>
  <tr>
    <th>Atributo</th>
    <th>Tipo de Dados</th>
    <th>Tamanho</th>
    <th>Restrições</th>
    <th>Descrição</th>
  </tr>
  <tr>
    <td>idTipoAgrotoxico</td>
    <td>INT</td>
    <td></td>
    <td>chave primária e obrigatório</td>
    <td>Número de identificação do tipo do agrotóxico</td>
  </tr>
  <tr>
    <td>nome</td>
    <td>VARCHAR</td>
    <td>80</td>
    <td>único e obrigatório</td>
    <td>Nome do tipo do agrotóxico</td>
  </tr>
</table>
<h6 align = "center">Tabela 10: Descrição Individual da tabela tabela TIPO_AGROTOXICO.</h6>
<h6 align = "center">Fonte: Autores</h6>

### 3.3 Descrição Individual das Tabelas de Relacionamento

<table id="dict">
  <tr>
    <th colspan="6">espera</th>
  </tr>
  <tr>
    <th>Atributo</th>
    <th>Tipo de Dados</th>
    <th>Tamanho</th>
    <th>Restrições</th>
    <th>Descrição</th>
  </tr>
  <tr>
    <td>idCultura</td>
    <td>INT</td>
    <td></td>
    <td>chave estrangeira, único e obrigatório</td>
    <td>Identificação da cultura</td>
  </tr>
  <tr>
    <td>idAgrotoxico</td>
    <td>INT</td>
    <td></td>
    <td>chave estrangeira, único e obrigatório</td>
    <td>Identificação do agrotóxico</td>
  </tr>
  <tr>
    <td>diasCarencia</td>
    <td>INT</td>
    <td></td>
    <td>obrigatório</td>
    <td>Intervalo de segurança em dias em o produtor pode colher o plantio após a aplicação do agrotóxico</td>
  <tr>
</table>
<h6 align = "center">Tabela 11: Descrição Individual da tabela espera.</h6>
<h6 align = "center">Fonte: Autores</h6>

<table id="dict">
  <tr>
    <th colspan="6">contem</th>
  </tr>
  <tr>
    <th>Atributo</th>
    <th>Tipo de Dados</th>
    <th>Tamanho</th>
    <th>Restrições</th>
    <th>Descrição</th>
  </tr>
  <tr>
    <td>idPlantio</td>
    <td>INT</td>
    <td></td>
    <td>chave estrangeira e obrigatório</td>
    <td>Identificação da carência</td>
  </tr>
  <tr>
    <td>idAgrotoxico</td>
    <td>INT</td>
    <td></td>
    <td>chave estrangeira e optativo</td>
    <td>Identificação do agrotóxico. Ela pode ser NULL até que um funcionário identifique o agrotóxico a partir da foto que o produtor tirou</td>
  </tr>
  <tr>
    <td>dataAplicacao</td>
    <td>DATE</td>
    <td></td>
    <td>obrigatório</td>
    <td>Data em que o produtor aplicou o agrotóxico</td>
  </tr>
  <tr>
    <td>caminhoFotoAgrotoxico</td>
    <td>VARCHAR</td>
    <td>255</td>
    <td>obrigatório</td>
    <td>Caminho para a foto do agrotóxico que o produtor aplicou no plantio</td>
  </tr>
  <tr>
    <td>estadoAnalise</td>
    <td>CHAR</td>
    <td>1</td>
    <td>obrigatório</td>
    <td>Estado da análise da aplicação. Podendo variar entre Sucesso, ComProblema, EmAnalise e etc.</td>
  </tr>
  <tr>
    <td>dosagemAplicacao</td>
    <td>DECIMAL</td>
    <td>6 dígitos e 2 casas decimais</td>
    <td>optativo</td>
    <td>Dosagem em litros da aplicação do agrotóxico.</td>
  </tr>
</table>
<h6 align = "center">Tabela 12: Descrição Individual da tabela contem.</h6>
<h6 align = "center">Fonte: Autores</h6>

## 4. Referências