<template>
  <TheHeader v-if="showHeader"/>
<input v-model="names" type="text" ><br>{{ names }}<br>
 <select v-model="pageCount">
  <option value="5">5</option>
  <option value="10">10</option>
  <option value="15">15</option>
 </select>
 {{ pageCount }}<br><br>

 <input v-model="user.firstName" type="text"> <input v-model="user.lastName" type="text"><br>
 {{ user.firstName }} e {{ user.lastName }}

  <br><br><br>
===============<br>
  Propriedade computada<br>
  <button @click="clico()">This</button><br><br>
  {{ fullName }}<br><br>
<b>tarefas em aberto</b><br>
  <div v-for="todo in uncompletedTodos" :key="todo.id">{{ todo.title}} - <span>{{ todo.completed }}</span></div>

  <b>tarefas completas</b>
  <div v-for="todo in completedTodos" :key="todo.id">{{ todo.title }} - {{ todo.completed }}</div>
  <br><br>
  <b>Todas as tarefas</b>
  <div v-for="todo in todos" :key="todo.id"><input type="checkbox" v-model="todo.completed">{{ todo.title }}</div>
  <br><br><br>
===============
  <form action="https://google.com" @submit.prevent="onSubmit">
    <button type="submit">Enviar google</button>
  </form>

  <input type="text" @keyup="onKeyUp" v-model="names" ><br><br> {{ names }} <br><br>

  <button @click.once="onClick()">Enviar</button><br><br>

  <div @mouseover="mouseOver()">Mouse Over</div>
  <div @mouseout="mouseOut">mouse out</div>

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

  <div v-if="showName">Nome: {{ user.firstName }} <br> Sobrenome: {{ user.lastName }}</div>
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
      pageCount: 5,
      colors: [] ,
      contrato: false ,
      newsletter: '' ,
      sports: '', 
      name: 'Tiago Bernardes',
      names: '',
      isHome: true,
      classVar: 'titulo',
      pClass: ['text', 'texto_home'],
      styleClass: {color : 'black', backgroundColor : 'aqua', fontSize : '20px'},
      showHeader: true,
      user: {firstName: 'Jhon', lastName: 'Snow'} ,
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
  },
  methods: {
        onClick() {console.log('mouse out')},
        mouseOver() {console.log('mouse over')},
        mouseOut($evt) {console.log('mouse out', $evt)},
        onSubmit() {console.log('submit')},
        onKeyUp($evt) {console.log('OnKeyUp', $evt)},
        clico() {console.log(this)},
        saveUserName() {console.log('Ajax'), console.log(this.names)},
        changePage() {console.log('Ajax changePage')}
      },
    computed: {
      fullName() {return `${this.user.firstName} ${this.user.lastName}`},
      uncompletedTodos() {return this.todos.filter(todo => !todo.completed)},
      completedTodos() {return this.todos.filter(todo => todo.completed)}
    },
    watch: {
      names(vl) {if (vl.length >= 3) {this.saveUserName()}},
      pageCount() {this.changePage()},
      user: { handler() {console.log('user alterado');}}, deep: true
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
