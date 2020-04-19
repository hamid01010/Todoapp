<template>
  <div class="home container">
    <h1 class="text-center">Todo app</h1>
    <br>
    <addtodo :todos="todos" v-on:add-todo="addtodo"/>
    <todos :todos="todos" v-on:del-todo="deletetodo" />
</div>
</template>

<script>
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
          this.todos = this.todos.filter((todo)=> todo.id !== id)
      },
      addtodo(newtodo){
          this.todos = [...this.todos, newtodo]
      }
  },
  data(){
      return{
          todos:[
              {
                  id: 1,
                  title: "jhjgjklhjklh",
                  completed: false
              },
              {
                  id: 2,
                  title: "vbbnvnbv",
                  completed: false
              }
          ]
      }
  }  
}
</script>

<style>

</style>