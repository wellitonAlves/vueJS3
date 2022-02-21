<template>
  <div>
    <p>{{ state }}</p>
    <button v-on:click="checkCep">Address</button>
    <button v-on:click="reiniciarEnd">Reiniciar</button>
    <p>{{ message }}</p>
    <p>{{ cep }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
    name: 'Address',
    props:{
      state:String,
      reiniciarEnd: Function,
      cep:String
    },
    data() {
      return {
        message:'',
        info: this.state,
      }
    },
    methods:{
      checkCep(){  
        // var axiosConfig = {
        //             headers: {
        //                 // 'Content-Type': 'application/x-www-form-urlencoded',
        //                 // // "Access-Control-Allow-Origin": "*",
        //                 // 'Accept': '*',
        //                Authorization: 'Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NCwiaWF0IjoxNjQ1MTI3OTgxLCJleHAiOjE2NDYxMTQzODF9.haKb0IOYsXI9GBdWzCG7PGeMow6yC8PwyNcGuBVdbno'
        //             }
        //         }

        //   axios               
        //     .get('https://backend-tarefa-teteu.herokuapp.com/tasks/', axiosConfig)
        //     .then(response => (console.log(response)))
        //     .catch(error => console.log(error, this.info = 'We can not find your CEP'))  

            // axios
            // .post('https://backend-tarefa-teteu.herokuapp.com/tasks/',{
            //   titulo:'17021705',
            //   description:'testeJose',
            // }, axiosConfig)
            // .then(response => (console.log(response)))
            // .catch(error => console.log(error, this.info = 'We can not find your CEP'))  

            //login sem o heder    
            // axios
            // .post('https://backend-tarefa-teteu.herokuapp.com/auth/create',{
            //   email:'teste@teste.com',
            //   username:'testeJose',
            //   password:'testeJose'
            // })
            // .then(response => (console.log(response)))
            // .catch(error => console.log(error, this.info = 'We can not find your CEP'))      

           axios
            .post('http://localhost:8090/address','teste')
            .then(response => (console.log(response)))
            .catch(error => console.log(error, this.info = 'We can not find your CEP'))

           this.$emit('enderecoMudou',{obj1:'Endereco1', obj2:'Endereco2'})
      },
    },
}

</script>

<style>

</style>