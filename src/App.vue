<script setup>

import {reactive, ref} from "vue";

const persons = reactive([
  {
    name: '',
    age: '',
    job: ''
  }
])

const memberArea = ref(true)

function newMemberAdder() {
  persons.push({
    name: '',
    age: '',
    job: ''
  })
}


</script>

<template>
<section class="flex flex-col justify-center items-center h-full space-y-10">
  <h1 class="font-bold text-5xl">Members Panel</h1>

<!--  <p>{{persons}}</p>-->

  <div class="flex flex-col space-y-5">
    <h2 class="text-2xl font-bold"> </h2>
    <div v-if="memberArea">
      <p class="italic">Sorry! No Member Found Yet...</p>
    </div>
    <div v-else v-for=" (person, index) in persons" :key="index" class="flex space-x-4">
      <div class="border rounded p-4 flex space-x-4">
  <p>index: {{index}}</p>
      </div>
      <div class="border rounded p-4 flex space-x-4">
        <p>Name: {{person.name}}</p>
        <p>Name: {{person.age}}</p>
        <p>Name: {{person.job}}</p>

      </div>
    </div>
  </div>

  <div class="flex space-y-5 flex-col justify-center items-center">
    <h2 class="text-2xl font-bold">Add New Member</h2>

    <form  class="flex flex-col space-y-4  space-x-4 sm:flex-row justify-center items-center" v-for=" (person, index) in persons" :key="index">
      <p>
        <label for="name">Name: </label>
        <input  @focus="memberArea = false" v-model="person.name" class="py-2 rounded border border-gray-500 px-2" type="text" id="name">
      </p>
      <p>
        <label for="age">Age: </label>
        <input  v-model="person.age" class="py-2 rounded border border-gray-500 px-2" type="number" id="age" >
      </p>
      <p>

        <label for="job">Job: </label>
        <input  v-model="person.job" class="py-2 rounded border border-gray-500 px-2" type="text" id="job">
      </p>

      <p>
        <button type="button" @click="persons.splice(index, 1)" class="bg-red-500 text-white px-4 py-2 rounded">Remove</button>
      </p>
    </form>
    <button @click="newMemberAdder(), memberArea = false"  class="bg-blue-500 text-white px-4 py-2 rounded w-[200px]">Add More Member</button>
  </div>

</section>

</template>

<style scoped>
</style>
