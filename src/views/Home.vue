<template>
    <component :is="selectedComponent"></component>
</template>

<script setup>
  import Aluno from './Aluno/Aluno.vue'
  import Instrutor from './Instrutor/Instrutor.vue'
  import { computed } from "vue";

  const selectedComponent = computed({
    get() {
      return localStorage.getItem('tipoUsuario') == 'Aluno' ? Aluno : Instrutor
    },
    set() {
      
    }
  })
  const tipoUser = computed(() => localStorage.getItem('tipoUsuario') == 'Aluno' ? 'aluno' : 'instrutor')
</script>

<style scoped>
  .alignCard{
    text-align: -webkit-center;  
  }

  div{
    color: white;
    background-color: #5c3551ff;
  }

  span{
    color: white;
  }

</style>