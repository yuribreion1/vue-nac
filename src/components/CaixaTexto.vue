<template>
    <input 
        :type="this.tipo" 
        :name="this.nome" 
        :id="this.identificador" 
        :value="this.valor" 
        :classe="this.classe"
        v-on:keyup="this.mudou"
        v-model="texto"
        />
</template>

<script>
export default {
    props: ['tipo','nome','identificador','valor','classe'],
    data() {
      return {
          texto: ""
      }  
    },
    methods: {
        mudou: function (event) {
            if(event.key=="Enter")
                this.$emit("pressionouEnter");
            else
                this.$emit("entrouDados", this.texto);
        }
    }
}
</script>

<style>
    input {
        margin: 10px 0 10px 0;
    }
</style>
