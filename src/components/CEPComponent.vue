<template>
  <div>
    <input v-model="message" />
    <button v-on:click="checkCep">search</button>
    <p>{{ cep }}</p>
    <p>{{ info }}</p>
    <button v-on:click="mostrarComponent">Mostrar componente</button>

    <Address 
    v-bind:state='info' 
    v-bind:cep='cep' 
    v-bind:reiniciarEnd="reiniciarEndereco" 
    @enderecoMudou="info = $event.obj2"
    /> 

    <div v-if=mostrar>
        <BrotherComponent 
              v-bind:state='info' 
              v-bind:cep='cep' 
              v-bind:reiniciarEnd="reiniciarEndereco"
            @enderecoMudou="info = $event.obj2"
            @cepMudou="cep = $event"
            >
            <template v-slot:texto1>
                <h1>Teste passando httl</h1>
            </template>
            <template v-slot:texto2>
                <h6>Teste passando html2</h6>
            </template>
        </BrotherComponent>
    </div>
   
    <!-- <BrotherComponent 
      v-bind:state='info' 
      v-bind:cep='cep' 
      v-bind:reiniciarEnd="reiniciarEndereco"
     @enderecoMudou="info = $event.obj2"
     @cepMudou="cep = $event"
     >
     <template v-slot:texto1>
        <h1>Teste passando httl</h1>
     </template>
     <template v-slot:texto2>
        <h6>Teste passando html2</h6>
     </template>
     </BrotherComponent> -->
  </div>
</template>

<script>
import axios from "axios";
import Address from './AddressComponent.vue'
import BrotherComponent from './NewComponent.vue'

export default {
  components: {
    Address,
    BrotherComponent
  },
    data() {
      return {
        message:'',
        info: '',
        cep:'03267070',
        mostrar:false
      }
    },
    methods:{
      checkCep(){
           axios
            .get('http://viacep.com.br/ws/'+this.message+'/json/')
            .then(response => (this.info = response))
            .catch(error => console.log(error, this.info = 'We can not find your CEP'))
      },
      reiniciarEndereco(){
        this.info = 'reiniciado'
      },
      mostrarComponent(){

          this.mostrar = this.mostrar ? false : true
      }
    },
}
</script>

<style scoped>

</style>
