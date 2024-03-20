<template>
  <TheHeader v-if="showHeader"/>

  <input type="text" v-model="name" /> <br> {{ name }}

  <div>
    <select v-model="sports">
    <option value="futebol">Futebol</option>
    <option value="skate">Skate</option>
    <option value="MTB">MTB</option>
    <option value="Tennis">Tennis</option>
    </select> <br> {{ sports }}
  </div>

  <div>
    <label>Newsletter</label>
    <input v-model="newsletter" type="radio" value="Sim">Sim
    <input v-model="newsletter" type="radio" value="Não"> Não
<br> {{ newsletter }}
  </div>

  <div>
    <label>Contrato</label>
    <input v-model="contrato" type="checkbox">Aceita nossos termos? <b>{{ contrato }}</b>
  </div>

  <div>
    <label>Cortes</label>
    <input v-model="colors" type="checkbox" value="Azul">Azul
    <input v-model="colors" type="checkbox" value="Amarelo">Amarelo
    <input v-model="colors" type="checkbox" value="Verde">Verde
    
    <br>{{ colors }}
  </div>



  <h1 :class="{ titulo : true, titulo_home : isHome }">Curso Vue 3</h1>

  <p :class="pClass">Loren ispsun</p>

  <p :style="styleClass">Outro parágrafo</p>

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
      colors: [] ,
      contrato: false ,
      newsletter: '' ,
      sports: '', 
      name: 'Tiago Bernardes',
      isHome: true,
      classVar: 'titulo',
      pClass: ['text', 'texto_home'],
      styleClass: {color : 'black', backgroundColor : 'aqua', fontSize : '20px'},
      showHeader: true,
      firstName: 'Jhon',
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

.titulo {font-size:20px;color:blue;}
.titulo_home {font-size:40px; color:green}
.texto {color:orange}
.texto_home {color:olive;}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
