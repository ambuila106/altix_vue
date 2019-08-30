<template>
  <div id="app">
    <img alt="Vue logo" v-bind:src="message">
    prueba
    <HelloWorld msg="Task "/>
    <ul>
      <li v-for="task in tasks">
        {{task.task_todo}}
      </li>
    </ul>
    <a ></a>{{message}}
  </div>
  
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'
export default {
  name: 'app',
  components: {
    HelloWorld
  },
  data(){
    return {
      tasks: [],
      message: '/img/logo.82b9c7a5.png'
    }
  },
  mounted(){
    axios.get('http://localhost:8000/api/task/')
    .then((response) => {
      // handle success
      console.log(response.data);
      this.tasks = response.data;
    })
    .catch(function (error) {
      // handle error
      console.log(error);
    })
    .finally(function () {
      // always executed
    });
  }
}
 
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
