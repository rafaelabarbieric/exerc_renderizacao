<script setup>
  import { computed, ref } from 'vue'

  let newCity = ref('')
  let listCitys = ref(['São Paulo','Rio de Janeiro','Belo Horizonte','Salvador','Fortaleza','Curitiba','Manaus','Recife','Porto Alegre','Brasília'])

  let organize = computed (() =>{
    return listCitys.value.sort()
  }
  )
  
  function add() {
    listCitys.value.push(newCity.value)
    newCity.value = ''
  }

  function deleteCity(item) {
    listCitys.value.splice(item, 1)
  }
  
</script>
<template>
  <input type="text" v-model="newCity">
  <button @click="add">Adicionar</button>
  <ul>
    <li v-for="item in organize">{{ item }} <button @click="deleteCity(item)">X</button></li>
  </ul>
</template>