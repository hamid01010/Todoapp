<template>
  <div class="home container">
    <h1 class="text-center">Todo app</h1>
    <br>
    <addtodo :todos="todos" v-on:add-todo="addtodo"/>
    <todos :todos="todos" v-on:del-todo="deletetodo" />
</div>
</template>

<script>
import axios from "axios"
import addtodo from "../components/Todoapp/Addtodo"
import todos from "../components/Todoapp/todos"
// @ is an alias to /src
export default {
  name: 'Home',
  components:{
      addtodo,
      todos
  },
  methods:{
      deletetodo(id){
          axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)//backticks are used in order to delete todo, we have to add id in the end of url (a variable) by adding slash
          .then(this.todos = this.todos.filter((todo)=> todo.id !== id))
          .catch(err => console.log(err))
      },
      addtodo(newtodo){
          const{title, completed} = newtodo//destructuring
          axios.post("https://jsonplaceholder.typicode.com/todos", {title, completed})
            .then(res => this.todos = [...this.todos, res.data])
            .catch(err => console.log(err))
      }
  },
  created(){
      axios.get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then(res => this.todos = res.data)
      .catch(err => console.log(err))
  },
  data(){
      return{
          todos:[]
      }
  }  
}
</script>

<style>

</style>