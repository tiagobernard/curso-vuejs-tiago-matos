<template>
  <TheHeader v-if="showHeader"/>

  <div v-if="showName">Nome: {{ firstName }} <br> Sobrenome: {{ lastName }}</div>

  <div v-for="(obj, index) in todos" :key="obj.id">
    <img v-if="obj.imgSrc" :src="obj.imgSrc" :alt="obj.title"/>
    {{ index }} - {{ obj.title }}
  </div>

  <div v-if="accessLevel === 'admin'">Admin</div>
  <div v-else-if="accessLevel === 'mkt'">Marketing</div>
  <div v-else>User</div>

  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>


<script>
import HelloWorld from './components/HelloWorld.vue'
import TheHeader from './components/TheHeader.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    TheHeader
  },
  data() {
    return {
      showHeader: true,
      firstName: 'Jhown',
      lastName: 'Snow' ,
      showName:  true,
      accessLevel: 'admin',
      todos: [
  {
    "userId": 1,
    "id": 1,
    "title": "delectus aut autem",
    "completed": false,
    "imgSrc": 'https://via.placeholder.com/150',
  },
  {
    "userId": 1,
    "id": 2,
    "title": "quis ut nam facilis et officia qui",
    "completed": false,
    "imgSrc": 'https://via.placeholder.com/150',
  },
  {
    "userId": 1,
    "id": 3,
    "title": "fugiat veniam minus",
    "completed": false,
    "imgSrc": 'https://via.placeholder.com/150',
  },
  {
    "userId": 1,
    "id": 4,
    "title": "et porro tempora",
    "completed": true

  },
  {
    "userId": 1,
    "id": 5,
    "title": "laboriosam mollitia et enim quasi adipisci quia provident illum",
    "completed": false
  }
]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
