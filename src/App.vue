<script setup>

import {ref} from 'vue'
let aux = ref([])
let tasks = ref([])
let inputName= '';
let inputPrioridad = '';

function addTask() {

let newTask = {
  name: inputName,
  prioridad: inputPrioridad,
}

tasks.value.push(newTask);

aux.value.push(newTask)


}

function deleteTask (index){

  tasks.value.splice(index ,1);

}

function actualizarDatos(index) {

  let newTask = {
  name: inputName,
  prioridad: inputPrioridad,
  }

  tasks.value[index] = newTask

  aux.value[index] = newTask

}


</script>

<template>


<input v-model="inputName" class="name" type="text"> 
<input v-model="inputPrioridad" class="prioridad" type="text">
  <button @click="addTask()">PRESIONAR</button>

  <div v-for="(obj, index) in tasks" :key="index">
  
    {{ obj.name }}
    {{ obj.prioridad }}

    <button @click="deleteTask(index)">BORRAR</button>
    <button @click="actualizarDatos(index)">Actualizar</button>

  </div>

<h1>----------------------------------------</h1>

  <div v-for="(xd, index ) in aux" :key="index">
    {{ xd.name }} {{ xd.prioridad }}
  </div>

  <h1>--------------------------</h1>

</template>
<style scoped>
</style>
