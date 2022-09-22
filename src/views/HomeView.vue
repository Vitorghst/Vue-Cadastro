<template id="app">
  <div class="margin-top">
    <div class="col-md-5 offset-md-2">
      <h3 class="box_header">Dados Pessoais</h3>
    </div>
    <div class="col-md-5 offset-md-2">
      <label>Nome completo</label>
      <input 
           v-model="fullname" 
           v-bind:class="{'form-control': true, 'is-invalid': !validName(fullname) && nameBlured , 'is-valid': validName(fullname)}"
           v-on:blur="nameBlured = true" >
        <div class="invalid-feedback">"Nome completo" não pode ficar em branco.</div>
    </div>
    <div class="col-md-5 offset-md-2">
      <div class="row">
        <div class="col-md-6 mt-5">
          <label>E-mail</label>
          <br>
          <input 
           v-model="email" 
           v-bind:class="{'form-control': true, 'is-invalid': !validEmail(email) && emailBlured , 'is-valid': validEmail(email)}"
           v-on:blur="emailBlured = true" >
        <div class="invalid-feedback">"E-mail" não pode ficar em branco.</div>
        </div>
        <div class="col-md-6 mt-5">
          <label>Senha</label>
          <br>
          <input 
           v-model="password" 
           v-bind:class="{'form-control': true, 'is-invalid': !validPassword(password) && passwordBlured , 'is-valid': validPassword(password)}"
           v-on:blur="passwordBlured = true" >
        <div class="invalid-feedback">"Senha" não pode ficar em branco.</div>
        </div>
      </div>
    </div>
    <div class="col-md-5 offset-md-2">
      <div class="row">
        <div class="col-md-6 mt-5">
          <label>Data de nascimento</label>
          <br>
          <input 
           v-model="dataNascimento" 
           v-bind:class="{'form-control': true, 'is-invalid': !validDataNasc(dataNascimento) && dataNascBlured , 'is-valid': validDataNasc(dataNascimento)}"
           v-on:blur="dataNascBlured = true" >
        <div class="invalid-feedback">"Data de nascimento" não pode ficar em branco.</div>
        </div>
        <div class="col-md-6 mt-5">
          <label>CPF</label>
          <br>
          <input 
           v-model="cpf" 
           v-bind:class="{'form-control': true, 'is-invalid': !validCpf(cpf) && cpfBlured , 'is-valid': validCpf(cpf)}"
           v-on:blur="cpfBlured = true" >
        <div class="invalid-feedback">"CPF" não pode ficar em branco.</div>
        </div>
      </div>
    </div>
    <div class="col-md-5 offset-md-2">
      <div class="row">
        <div class="col-md-6 mt-5">
          <label>Possui filhos ou dependentes?</label>
          <div class="mb-3">
            <select class="form-select" v-model="possuiFilhosDependentes" 
           v-bind:class="{'form-control': true, 'is-invalid': !validFilhosDep(possuiFilhosDependentes) && filhosDepBlured, 'is-valid': validFilhosDep(possuiFilhosDependentes)}"
           v-on:blur="filhosDepBlured = true" >
              <option value="">Selecione</option>
              <option value="1">Sim</option>
              <option value="2">Não</option>
            </select>
            <div class="invalid-feedback">"Possui filhos ou dependentes?" não pode ficar em branco.</div>
          </div>
        </div>
        <div class="col-md-6 mt-5">
          <label class="mb-1">Quantos filhos ou dependentes?</label>
          <div class="mb-3">
            <select class="form-select" v-model="quantosFilhosDependentes" 
           v-bind:class="{'form-control': true, 'is-invalid': !validQuantosDep(quantosFilhosDependentes) && quantosDepBlured, 'is-valid': validQuantosDep(quantosFilhosDependentes)}"
           v-on:blur="quantosDepBlured = true" >
              <option value="">Selecione</option>
              <option value="1">Não Possui</option>
              <option value="2">1</option>
              <option value="3">2</option>
              <option value="4">3</option>
              <option value="5">4</option>
              <option value="2">Mais de 5</option>
            </select>
            <div class="invalid-feedback">"Quantos filhos ou dependentes?" não pode ficar em branco.</div>
          </div>
        </div>
      </div>
    </div>
    <div class="col-md-5 offset-md-2">
      <div class="row">
        <div class="col-md-6 mt-5">
          <label>Estado cívil</label>
          <div class="mb-3">
            <select class="form-select" v-model="estadoCivil" 
           v-bind:class="{'form-control': true, 'is-invalid': !validEstadoCivil(estadoCivil) && estadoCivilBlured, 'is-valid': validEstadoCivil(estadoCivil)}"
           v-on:blur="estadoCivilBlured = true"  >
              <option value="">Selecione</option>
              <option value="1">Casado</option>
              <option value="2">Solteiro</option>
              <option value="3">Divorciado</option>
              <option value="4">Viúvo</option>
            </select>
            <div class="invalid-feedback">"Estado cívil" não pode ficar em branco.</div>
          </div>
        </div>
        <div class="col-md-6 mt-5">
          <label class="mb-1">Sexo</label>
          <div class="mb-3">
            <select class="form-select" v-model="sexo" 
           v-bind:class="{'form-control': true, 'is-invalid': !validSexo(sexo) && sexoBlured, 'is-valid': validSexo(sexo)}"
           v-on:blur="sexoBlured = true" >
              <option value="">Selecione</option>
              <option value="1">Masculino</option>
              <option value="2">Feminino</option>
            </select>
            <div class="invalid-feedback">"Sexo" não pode ficar em branco.</div>
          </div>
        </div>
      </div>
    </div>
    <div class="col-md-5 offset-md-2">
      <div class="row">
        <div class="col-md-3 mt-5">
          <label>CEP</label>
          <div class="mb-3">
            <input 
            id="cep"
           v-model="cep" 
           v-bind:class="{'form-control': true, 'is-invalid': !validCep(cep) && cepBlured, 'is-valid': validCep(cep)}"
           v-on:blur="cepBlured = true" @keyup="searchCep()" >
            <div class="invalid-feedback">"CEP" não pode ficar em branco.</div>
          </div>
          <small>Seu endereço será preenchido automaticamente</small>
        </div>
      </div>
    </div>
    <div class="col-md-6 offset-md-2">
      <div class="row">
        <div class="col-md-6 mt-5">
          <label>Endereço</label>
          <br>
          <input 
           id="logradouro"
           v-model="endereco" 
           v-bind:class="{'form-control': true, 'is-invalid': !validEndereco(endereco) && enderecoBlured, 'is-valid': validEndereco(endereco)}"
           v-on:blur="enderecoBlured = true" >
           <small class="invalid-feedback">"Endereço" não pode ficar em branco.</small>
        </div>
        
        <div class="col-md-4 mt-5">
          <label>Número</label>
          <br>
          <input 
           id="numero"
           v-model="numero" 
           v-bind:class="{'form-control': true, 'is-invalid': !validNumero(numero) && numeroBlured, 'is-valid': validNumero(numero)}"
           v-on:blur="numeroBlured = true" >
           <small class="invalid-feedback">"Número" não pode ficar em branco.</small>
        </div>
      </div>
    </div>
    <div class="col-md-5 offset-md-2">
      <div class="row">
        <div class="col-md-6 mt-5">
          <label>Complemento</label>
          <br>
          <input 
           id="complemento"
           v-model="complemento" 
           v-bind:class="{'form-control': true, 'is-valid': validComplemento(complemento) && complementoBlured ,  'is-valid': !validComplemento(complemento)}"
           v-on:blur="complementoBlured = true" >
           <small class="invalid-feedback">"Complemento" não pode ficar em branco.</small>
        </div>
        <div class="col-md-6 mt-5">
          <label>Bairro</label>
          <br>
          <input 
           id="bairro"
           v-model="bairro" 
           v-bind:class="{'form-control': true, 'is-invalid': !validBairro(bairro) && bairroBlured, 'is-valid': validBairro(bairro)}"
           v-on:blur="bairroBlured = true" >
           <small class="invalid-feedback">"Bairro" não pode ficar em branco.</small>
        </div>
      </div>
    </div>
    <div class="col-md-5 offset-md-2">
      <div class="row">
        <div class="col-md-6 mt-5">
          <label>Estado</label>
          <div class="mb-3">
            <select class="form-select" id="uf"
           v-model="estado" 
           v-bind:class="{'form-control': true, 'is-invalid': !validEstado(estado) && estadoBlured, 'is-valid': validEstado(estado)}"
           v-on:blur="estadoBlured = true">
              <option value="">Selecione</option>
              <option value="1">AC</option>
              <option value="2">AL</option>
              <option value="3">AP</option> 
              <option value="4">AM</option>
              <option value="5">BA</option>
              <option value="6">CE</option>
              <option value="7">DF</option>
              <option value="8">ES</option>
              <option value="9">GO</option>
              <option value="10">MA</option>
              <option value="11">MT</option>
              <option value="12">MS</option>
              <option value="13">MG</option>
              <option value="14">PA</option>
              <option value="15">PB</option>
              <option value="16">PR</option>
              <option value="17">PE</option>
              <option value="18">PI</option>
              <option value="19">RJ</option>
              <option value="20">RN</option>
              <option value="21">RS</option>
              <option value="22">RO</option>
              <option value="23">RR</option>
              <option value="24">SC</option>
              <option value="25">SP</option>
              <option value="26">SE</option>
              <option value="27">TO</option>
              
              
            </select>
            <div class="invalid-feedback">"Estado" não pode ficar em branco.</div>
          </div>
        </div>
        <div class="col-md-6 mt-5">
          <label class="mb-1">Cidade</label>
          <div class="mb-3">
            <select class="form-select" id="localidade" 
            v-model="cidade" 
           v-bind:class="{'form-control': true, 'is-invalid': !validCidade(cidade) && estadoBlured, 'is-valid': validCidade(cidade)}"
           v-on:blur="cidadeBlured = true">
              <option value="">Selecione</option>
              <option value="1">Rolandia</option>
              <option value="2">Londrina</option>
            </select>
            <div class="invalid-feedback">"Cidade" não pode ficar em branco.</div>
          </div>
        </div>
      </div>
    </div>
    <div class="col-md-5 offset-md-2">
      <div class="row">
        <div class="col-md-6 mt-5">
          <label>Telefone Residencial</label>
          <br>
          <input 
           v-model="telefoneResi" 
           v-bind:class="{'form-control': true, 'is-invalid': !validtelefoneResi(telefoneResi) && telefoneResiBlured ,  'is-valid': validtelefoneResi(telefoneResi)}"
           v-on:blur="telefoneResiBlured = true" />
            <small class="invalid-feedback">"Telefone Residencial" não pode ficar em branco.</small>
        </div>
        <div class="col-md-6 mt-5">
          <label>Telefone Comercial</label>
          <br>
          <input 
           v-model="telefoneComer" 
           v-bind:class="{'form-control': true, 'is-valid': validtelefoneComer(telefoneComer) && telefoneComerBlured ,  'is-valid': validtelefoneComer(telefoneComer)}"
           v-on:blur="telefoneComerBlured = true" />
            <small class="invalid-feedback">"Telefone Comercial" não pode ficar em branco.</small>
        </div>
      </div>
    </div>
    <div class="col-md-5 offset-md-2">
      <div class="row">
        <div class="col-md-6 mt-5">
          <label>Telefone de Contato</label>
          <br>
          <input 
           v-model="telefoneContato" 
           v-bind:class="{'form-control': true, 'is-valid': validtelefoneContato(telefoneContato) && telefoneContatoBlured ,  'is-valid': validtelefoneContato(telefoneContato)}"
           v-on:blur="telefoneContatoBlured = true" />
            <small class="invalid-feedback">"Telefone de Contato" não pode ficar em branco.</small>
        </div>
        <div class="col-md-6 mt-5">
          <label>Ramal</label>
          <br>
          <input 
           v-model="ramal" 
           v-bind:class="{'form-control': true, 'is-valid': validRamal(ramal) && ramalBlured ,  'is-valid': validRamal(ramal)}"
           v-on:blur="ramalBlured = true" />
            <small class="invalid-feedback">"Ramal" não pode ficar em branco.</small>
        </div>
      </div>
    </div>
    <div class="col-md-5 offset-md-2">
      <label>Telefone Celular</label>
       <input 
           v-model="telefoneCelular" 
           v-bind:class="{'form-control': true, 'is-valid': validtelefoneCelular(telefoneCelular) && telefoneCelularBlured ,  'is-valid': validtelefoneCelular(telefoneCelular)}"
           v-on:blur="telefoneCelularBlured = true" />
            <small class="invalid-feedback">"Telefone Celular" não pode ficar em branco.</small>
    </div>
    <div class="col-md-5 offset-md-2">
      <div class="row">
        <div class="col-md-6 mt-5">
          <label>Possui alguma deficiência?</label>
          <div class="mb-3">
            <select class="form-select" v-model="possuiDeficiencia"
           v-bind:class="{'form-control': true, 'is-invalid': !validPossuiDeficiencia(possuiDeficiencia) && possuiDeficienciaBlured ,  'is-valid': validPossuiDeficiencia(possuiDeficiencia)}"
           v-on:blur="possuiDeficienciaBlured = true">
              <option value="">Selecione</option>
              <option value="1">Não</option>
              <option value="2">Sim</option>
            </select>
            <div class="invalid-feedback">"Possui alguma deficiência?" não pode ficar em branco.</div>
          </div>
        </div>
        <div class="col-md-6 mt-5">
          <label>Qual deficiência?</label>
          <br>
          <input 
           v-model="qualDeficiencia" 
           v-bind:class="{'form-control': true, 'is-valid': validQualDeficiencia(qualDeficiencia) && qualDeficienciaBlured ,  'is-valid': validQualDeficiencia(qualDeficiencia)}"
           v-on:blur="qualDeficienciaBlured = true" />
            <small class="invalid-feedback">"Qual deficiência?" não pode ficar em branco.</small>
        </div>
      </div>
    </div>
    <div class="col-md-5 offset-md-2">
      <h3 class="box_header">Formação Complementar</h3>
    </div>
    <div id="clone">
      <div class="col-md-5 offset-md-2">
        <h4 class="box_header font-weight-bolder text-smalt-blue text-uppercase">Curso <span id="count"> 1</span></h4>

      </div>
      <div class="col-md-5 offset-md-2">
        <div class="row">
          <div class="col-md-6 mt-5">
            <label class="mb-1">Formação</label>
            <div class="mb-3">
              <select class="form-select">
                <option value="">Selecione</option>
                <option value="2">1º Grau (5º a 9º Série)</option>
                <option value="3">2º Grau (1º a 3º Ano)</option>
                <option value="5">3º Grau (Graduação)</option>
                <option value="1">Ensino Fundamental (1º a 4º Série)</option>
                <option value="9">Pós Graduação (Doutorado)</option>
                <option value="6">Pós Graduação (Especialização)</option>
                <option value="7">Pós Graduação (MBA)</option>
                <option value="8">Pós Graduação (Mestrado)</option>
              </select>
            </div>
          </div>
          <div class="col-md-6 mt-5">
            <label>Curso</label>
            <br>
            <input v-model="message" class="form-control" />
          </div>
        </div>
      </div>
      <div class="col-md-5 offset-md-2">
        <div class="row">
          <div class="col-md-6 mt-5">
            <label class="mb-1">Situação do Curso</label>
            <div class="mb-3">
              <select class="form-select">
                <option value="">Selecione</option>
                <option value="1">Concluído</option>
                <option value="2">Cursando</option>
                <option value="3">Trancado</option>
              </select>
            </div>
          </div>
          <div class="col-md-6 mt-5">
            <label>Mês e Ano de conclusão</label>
            <br>
            <input v-model="message" class="form-control" />
          </div>
        </div>
      </div>
      <div class="col-md-5 offset-md-2">
        <div class="row">
          <div class="col-md-6 mt-5">
            <label class="mb-1">Turno</label>
            <div class="mb-3">
              <select class="form-select">
                <option value="">Selecione</option>
                <option value="M">Matutino</option>
                <option value="V">Vespertino</option>
                <option value="N">Noturno</option>
                <option value="I">Integral</option>
              </select>
            </div>
          </div>
          <div class="col-md-6 mt-5">
            <label>Instituição</label>
            <br>
            <input v-model="message" class="form-control" />
          </div>
        </div>
      </div>
    </div>
    <div id="clone2">
    </div>
    <div class="col-md-5 offset-md-2">
      <div class="text-right col-md-12 mt-4">
        <button class="more blue add-formation" type="button" @click="Clone()">+ Formação Complementar</button>
      </div>
    </div>
    <div class="col-md-5 offset-md-2">
      <h3 class="box_header">Cursos Adicionais</h3>
    </div>
    <div class="col-md-5 offset-md-2">
      <div class="row">
        <div class="col-md-6 mt-5">
          <label>Nível de Experiência em Espanhol</label>
          <div class="mb-3">
            <select class="form-select">
              <option value="">Selecione</option>
              <option value="N">Nenhuma</option>
              <option value="B">Básico</option>
              <option value="I">Intermediário</option>
              <option value="A">Avançado</option>
            </select>
          </div>
        </div>
        <div class="col-md-6 mt-5">
          <label class="mb-1">Nível de Experiência em Excel</label>
          <div class="mb-3">
            <select class="form-select">
              <option value="">Selecione</option>
              <option value="N">Nenhuma</option>
              <option value="B">Básico</option>
              <option value="I">Intermediário</option>
              <option value="A">Avançado</option>
            </select>
          </div>
        </div>
      </div>
    </div>
    <div class="col-md-5 offset-md-2">
      <div class="row">
        <div class="col-md-6 mt-5">
          <label>Nível de Experiência em Informática</label>
          <div class="mb-3">
            <select class="form-select">
              <option value="">Selecione</option>
              <option value="N">Nenhuma</option>
              <option value="B">Básico</option>
              <option value="I">Intermediário</option>
              <option value="A">Avançado</option>
            </select>
          </div>
        </div>
        <div class="col-md-6 mt-5">
          <label class="mb-1">Nível de Experiência em Inglês</label>
          <div class="mb-3">
            <select class="form-select">
              <option value="">Selecione</option>
              <option value="N">Nenhuma</option>
              <option value="B">Básico</option>
              <option value="I">Intermediário</option>
              <option value="A">Avançado</option>
            </select>
          </div>
        </div>
      </div>
    </div>
    <div class="col-md-5 offset-md-2">
      <div class="row">
        <div class="col-md-6 mt-5">
          <label>Nível de Experiência em Internet</label>
          <div class="mb-3">
            <select class="form-select">
              <option value="">Selecione</option>
              <option value="N">Nenhuma</option>
              <option value="B">Básico</option>
              <option value="I">Intermediário</option>
              <option value="A">Avançado</option>
            </select>
          </div>
        </div>
        <div class="col-md-6 mt-5">
          <label class="mb-1">Nível de Experiência em PowerPoint</label>
          <div class="mb-3">
            <select class="form-select">
              <option value="">Selecione</option>
              <option value="N">Nenhuma</option>
              <option value="B">Básico</option>
              <option value="I">Intermediário</option>
              <option value="A">Avançado</option>
            </select>
          </div>
        </div>
      </div>
    </div>
    <div class="col-md-5 offset-md-2">
      <div class="row">
        <div class="col-md-6 mt-5">
          <label>Nível de Experiência em Word</label>
          <div class="mb-3">
            <select class="form-select">
              <option value="">Selecione</option>
              <option value="N">Nenhuma</option>
              <option value="B">Básico</option>
              <option value="I">Intermediário</option>
              <option value="A">Avançado</option>
            </select>
          </div>
        </div>
      </div>
    </div>
    <div class="col-md-6 offset-md-2">
      <div class="row">
        <div class="col-md-10 mt-5">
          <label>Outros</label>
          <br>
          <input v-model="message" class="form-control" />
        </div>
      </div>
    </div>
    <div class="col-md-5 offset-md-2">
      <h3 class="box_header">Experiência Profissional</h3>
    </div>
    <div id="cloneExperience">

      <div class="col-md-5 offset-md-2" id="count">
        <h4 class="box_header font-weight-bolder text-smalt-blue text-uppercase">EXPERIÊNCIA<span> 1</span>
        </h4>
      </div>
      <div class="col-md-5 offset-md-2">
        <div class="row">
          <div class="col-md-6 mt-5">
            <label>Empresa</label>
            <br>
            <input class="form-control" />
          </div>
          <div class="col-md-6 mt-5">
            <label>Cargo</label>
            <br>
            <input class="form-control" />
          </div>
        </div>
      </div>
      <div class="col-md-5 offset-md-2">
        <div class="row">
          <div class="col-md-6 mt-5">
            <label>Período de</label>
            <br>
            <input class="form-control" />
          </div>
          <div class="col-md-6 mt-5">
            <label>até</label>
            <br>
            <input class="form-control" />
          </div>
        </div>
      </div>
    </div>
    <div id="cloneExperience2">
      <div id="count2">

      </div>
    </div>

    <div class="col-md-5 offset-md-2">
      <div class="text-right col-md-12 mt-4">
        <button class="more blue add-formation" type="button" @click="CloneExperience()">+ Experiência
          Profissional</button>
      </div>
    </div>


    <div class="col-md-5 offset-md-2">
      <h3 class="box_header">Informação Adicionais</h3>
    </div>
    <div class="col-md-6 offset-md-2 ">
      <div class="row ">
        <div class="col-md-10 mt-5 ">
          <label>Informações adicionais</label>
          <br>
          <textarea class="form-control height-100 " aria-invalid="false"
          v-model="adicionais" 
           v-bind:class="{'form-control': true, 'is-valid': validAdicionais(adicionais) && adicionaisBlured ,  'is-valid': validAdicionais(adicionais)}"
           v-on:blur="adicionaisBlured = true"  ></textarea>
        </div>
        <div class="col-md-10 mt-5">
          <label>Disponibilidade de horário</label>
          <div class="mb-3">
            <select class="form-select" 
            v-model="disponibilidade" 
           v-bind:class="{'form-control': true, 'is-invalid': !validDisponibilidade(disponibilidade) && disponibilidadeBlured ,  'is-valid': validDisponibilidade(disponibilidade)}"
           v-on:blur="disponibilidadeBlured = true" >
              <option value="">Selecione</option>
              <option value="">Selecione</option>
              <option value="M">Manhã</option>
              <option value="T">Tarde</option>
              <option value="N">Noite</option>
              <option value="I">Integral</option>
            </select>
            <span class="invalid-feedback" v-if="!validDisponibilidade(disponibilidade) && disponibilidadeBlured">Selecione uma opção</span>
          </div>
        </div>
        <div class="col-md-10 mt-5">
          <label>Área pretendida</label>
          <div class="mb-3">
            <select class="form-select" 
            v-model="area" 
           v-bind:class="{'form-control': true, 'is-invalid': !validArea(area) && areaBlured ,  'is-valid': validArea(area)}"
           v-on:blur="areaBlured = true" >
              <option value="">Selecione</option>
              <option value="20">Administrativo</option>
              <option value="19">Aprendizes</option>
              <option value="23">Central de Guias</option>
              <option value="2">Compras</option>
              <option value="10">Comunicação</option>
              <option value="22">Contabilidade</option>
              <option value="3">Copa</option>
              <option value="4">Enfermagem</option>
              <option value="5">Farmácia</option>
              <option value="6">Faturamento</option>
              <option value="7">Financeiro</option>
              <option value="8">Fisioterapia</option>
              <option value="9">Informática</option>
              <option value="11">Limpeza</option>
              <option value="18">Medicina do Trabalho</option>
              <option value="21">Motorista</option>
              <option value="12">Nutrição</option>
              <option value="14">Portaria</option>
              <option value="13">Psicologia</option>
              <option value="15">Recepção</option>
              <option value="16">Recursos Humanos</option>
              <option value="1">Serviço Social</option>
              <option value="17">Tesouraria</option>
            </select>
            <span class="invalid-feedback" v-if="!validArea(area) && areaBlured">Selecione uma opção</span>
          </div>
        </div>
        <div class="col-md-10 mt-5">
          <label>Função</label>
          <div class="mb-3">
            <select class="form-select" 
            v-model="funcao" 
           v-bind:class="{'form-control': true, 'is-invalid': !validFuncao(funcao) && funcaoBlured ,  'is-valid': validFuncao(funcao)}"
           v-on:blur="funcaoBlured = true">
              <option value="">Selecione</option>
              <option value="46">Jovem Aprendiz (de 17 a 18 anos)</option>
            </select>
            <span class="invalid-feedback" v-if="!validFuncao(funcao) && funcaoBlured">Selecione uma opção</span>
          </div>
        </div>
      </div>
      <button type="submit" class="more blue mb-4  mt-3">Enviar</button>
    </div>

  </div>

</template>
   
<script>

import axios from "axios";
import { required } from '@vuelidate/validators'

export default {
  el: "#app",
  data() {
    return {
      cep: "",
      address: {},
      count: 1,
      countExpericence: 1,
      email: "",
      fullname: "",
      estado: "",
      senha: "",
      dataNascimento: "",
      cpf: "",
      numero : "",
      password: "",
      possuiFilhosDependentes: "",
      quantosFilhosDependentes: "",
      estadoCivil: "",
      sexo: "",
      endereco: "",
      area: "",
      funcao: "",
      cidade: "",
      bairro: "",
      telefoneResi: "",
      telefoneComer: "",
      telefoneCelular: "",
      ramal: "",
      adicionais: "",
      telefoneContato: "",
      qualDeficiencia: "",
      disponibilidade: "",
      disponibilidadeBlured: false,
      qualDeficienciaBlured: false,
      areaBlured: false,
      funcaoBlured: false,
      possuiDeficiencia: "",
      possuiDeficienciaBlured: false,
      adicionaisBlured: false,
      telefoneCelularBlured: false,
      ramalBlured: false,
      telefoneContatoBlured: false,
      telefoneResiBlured: false,
      telefoneComerBlured: false,
      valid : true, 
      passwordBlured: false,
      sexoBlured: false,
      estadoCivilBlured: false,
      nameBlured : false,
      emailBlured: false,
      dataNascBlured: false,
      enderecoBlured: false,
      cpfBlured: false,
      estadoBlured: false,
      filhosDepBlured: false,
      cidadeBlured: false,
      numeroBlured: false,
      complementoBlured: false,
      cepBlured: false,
      bairroBlured: false,
      quantosDepBlured: false,
    }

  },
  validations() {
    return {
      fullname: {
        required
      },
      email: {
        required
      }
    }
  },
  methods: {
    searchCep() {
      axios
        .get(`https://viacep.com.br/ws/${this.cep}/json/`)
        .then((response) => {
          this.address = response.data;
          document.getElementById("logradouro").value = this.address.logradouro;
          document.getElementById("bairro").value = this.address.bairro;
          document.getElementById("localidade").value = this.address.localidade;
          document.getElementById("uf").value = this.address.uf;

          var opt = document.createElement('option');
          opt.value = this.address.localidade;
          opt.innerHTML = this.address.localidade;
          document.getElementById("localidade").appendChild(opt);

          var opt2 = document.createElement('option');
          opt2.innerHTML = this.address.uf;
          opt2.value = this.address.uf;
          document.getElementById("uf").appendChild(opt2);
          // option of select with value of uf
          console.log(this.address);
        })
        // depois que limpar o campo, limpar o objeto 
        .catch((error) => {
          this.address = {};
          document.getElementById("logradouro").value = "";
          document.getElementById("bairro").value = "";
          document.getElementById("localidade").value = "";
          document.getElementById("uf").value = "";
          console.log(error);
        });
    },

    validate : function(){
      this.nameBlured = true;
       if( this.validName(this.fullname)){
          this.valid = true;
       }
      this.emailBlured = true;
      if( this.validEmail(this.email)){
        this.valid = true;
      }
    },

    validEmail : function(email){
      if(email == ""){
        return false;
      }
      return true;
    },

    validPossuiDeficiencia : function(possuiDeficiencia){
      if(possuiDeficiencia == ""){
        return false;
      }
      return true;
    },

    validFuncao : function(funcao){
      if(funcao == ""){
        return false;
      }
      return true;
    },

    validArea : function(area){
      if(area == ""){
        return false;
      }
      return true;
    },
    
    validName : function(){
      if(this.fullname.length < 3){
        return false ;
        
      }
      return true + 'is-valid';
    },

    validQualDeficiencia : function(qualDeficiencia){
      if(qualDeficiencia == ""){
        return false;
      }
      return true;
    },

    validAdicionais : function(adicionais){
      if(adicionais == ""){
        return false;
      }
      return true;
    },


    validPassword : function(){
      if(this.password.length < 6){
        return false;
      }
      return true;
    },

    validDataNasc : function(){
      if(this.dataNascimento == ""){
        return false;
      }
      return true;
    },

    validEstado : function(){
      if(this.estado == ""){
        return false;
      }
      return true;
    },

    validCpf : function(){
      if(this.cpf == ""){
        return false;
      }
      return true;
    },

    validFilhosDep : function(){
      if(this.possuiFilhosDependentes == ""){
        return false;
      }
      return true;
    },

    validQuantosDep : function(){
      if(this.quantosFilhosDependentes == ""){
        return false;
      }
      return true;
    },

    validSexo : function(){
      if(this.sexo == ""){
        return false;
      }
      return true;
    },

    validEstadoCivil : function(){
      if(this.estadoCivil == ""){
        return false;
      }
      return true;
    },

    validCep : function(){
      if(this.cep == ""){
        return false;
      }
      return true;
    },

    validEndereco : function(){
      if(this.endereco == ""){
        return false;
      }
      return true;
    },

    validNumero : function(){
      if(this.numero == ""){
        return false;
      }
      return true;
    },

    validtelefoneContato : function(){
      if(this.telefoneContato == ""){
        return false;
      }
      return true;
    },

    validDisponibilidade : function(){
      if(this.disponibilidade == ""){
        return false;
      }
      return true;
    },

    validRamal : function(){
      if(this.ramal == ""){
        return false;
      }
      return true;
    },

    validtelefoneCelular : function(){
      if(this.telefoneCelular == ""){
        return false;
      }
      return true;
    },

    validComplemento : function(){
      if(this.complemento == ""){
        return false;
      }
      return true;
    },

    validBairro : function(){
      if(this.bairro == ""){
        return false;
      }
      return true;
    },

    validCidade : function(){
      if(this.cidade == ""){
        return false;
      }
      return true;
    },
    
    validtelefoneResi: function(){
      if(this.telefoneResi == ""){
        return false;
      }
      return true;
    },

    validtelefoneComer: function(){
      if(this.telefoneComer == ""){
        return false;
      }
      return true;
    },




    submit: function () {

      this.$v.$touch();
      if (this.$v.$pendding || this.$v.$error) return;

      alert('Data Submit');
    },

     //mudar o valor 01 para o valor do count 
    Clone() {
      const node = document.getElementById("clone");
      const clone = node.cloneNode(true);
      document.getElementById("count").appendChild(clone);
      this.count++;
      clone.querySelector("h4").innerHTML = `Curso  ${this.count}`;
      document.getElementById("clone2").appendChild(clone);
    },

    CloneExperience() {
      const node = document.getElementById("cloneExperience");
      const clone = node.cloneNode(true);
      this.countExpericence++;
      clone.querySelector("h4").innerHTML = `Experiência  ${this.countExpericence}`;
      document.getElementById("cloneExperience2").appendChild(clone);
    },

  },
};



</script>

<style>
h3.box_header {
  margin: 0 0 20px;
  font-weight: bold;
  font-size: 24px;
  margin: 20px 0 10px;
  font-weight: 400;
  border-bottom: 2px solid #DDD;
  /* color: #45b3ee; */
  padding-bottom: 15px;
  line-height: 30px;
}

.height-100 {
  height: 150px !important;
}

.more.dark_blue,
.more.light,
.more.blue,
.more.red {
  padding: 10px 30px;
  color: #FFF;
  border: 1px solid #FFF;
}

.more.blue {
  font-size: 1em;
  font-weight: 600;
  line-height: 34px;
}

.more {
  background: #FFFFFF;
  text-transform: uppercase;
  text-decoration: initial;
}

.more.blue {
  /* border-color: #3156A3; */
  background-color: #0072B4;
}

* {
  font-family: helvetica-w01-roman, helvetica-w02-roman, helvetica-lt-w10-roman, sans-serif;
}

h4 {
  font-size: 1em;
  margin: 1.33em 0;
  line-height: 20px;
}


.form-control {
  display: block;
  width: 100%;
  height: calc(1.5em + 0.75rem + 2px);
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  font-weight: 400;
  line-height: 1.5;
  color: #495057;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ced4da;
  border-radius: 0.25rem;
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}

label {
  margin-bottom: 0.5rem;
}

hr {
  margin-left: 20%;
  width: 20%;
}

.text-smalt-blue {
  color: #4F8987;
}

.font-weight-bolder {
  font-weight: bolder !important;
}

.border {
  border-style: 2px solid #000;
}
</style>