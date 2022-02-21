<template>
  <div>
    <p>{{ state }}</p>
    <button v-on:click="alteraCep">Mudar Cep</button>
    <p>{{ cep }}</p>
    <slot name="texto1"></slot>
    <slot name="texto2"></slot>
  </div>
</template>

<script>
export default {
    name: 'BrotherComponent',
    props:{
      state:String,
      cep:String,
    },
    data() {
      return {
        message:'',
        info: this.state,
      }
    },
    methods:{
      alteraCep(){
          this.$emit('cepMudou','0001110')
      }
    },
}

</script>

<style>

</style>