<template>
    <input :type="this.tipo" :class="this.classe" v-on:click="clicou" :name="this.nome" :value="this.valor" >
</template>

<script>
export default {
    props: ['tipo','nome','valor','classe'] , 
    methods: {
        clicou : function () {
        this.$emit("clicou");
        }
  }
}
</script>

<style>
    input {
        margin: 10px 0 10px 0;
        display: block;
    }
</style>
