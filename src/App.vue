<template>
  <div id="app" class="container">
    <Titulo classe="display-5" />
    <Descricao descricao="Nome: " />
    <CaixaTexto v-on:entrouDados="atualizaNome" classe="form-control" tipo="text" nome="nome" ref="entradaNome" />
    <Descricao descricao="Telefone: " />
    <CaixaTexto v-on:entrouDados="atualizaTelefone" classe="form-control" tipo="text" nome="telefone" ref="entradaTelefone" />
    <Botao classe="btn btn-primary" tipo="button" valor="Adicionar" v-on:clicou="this.atualizaContato"/>
    <ul>
      <li :key="indice" v-for="(contato, indice) in contatos">
        {{ contato.nome }} - {{ contato. telefone }} 
        <Botao valor="Remover" tipo="button" classe="btn btn-primary" v-on:clicou="removeContato" />
      </li>
    </ul>
  </div>
</template>

<script>

import Titulo from './components/Titulo.vue'
import Botao from './components/Botao.vue'
import CaixaTexto from './components/CaixaTexto.vue'
import Descricao from './components/Descricao.vue'

export default {
  name: 'app',
  components: {
    Titulo
    , Botao
    , CaixaTexto
    , Descricao
  }, data() {
    return {
      contatos: [],
      textoNome: "",
      textoTelefone: ""

    }
  }, methods: {
    atualizaNome(nome){
      this.textoNome = nome;
      console.log(nome);
    }, atualizaTelefone(telefone){
      this.textoTelefone = telefone;
      console.log(telefone);
    }, atualizaContato: function () {
      this.contatos.push({
        nome: this.textoNome,
        telefone: this.textoTelefone
      })
      console.log(this.contatos); 
    }, removeContato: function () {
      this.contatos.pop();
    }
  }
}
</script>

<style lang="scss">
  @import './assets/styles/variables';
  @import './assets/styles/bootstrap';
  li {
    margin: 10px 0 10px 0;
  }
</style>
