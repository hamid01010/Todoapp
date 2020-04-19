<template>
  <div>
      <div v-for="todo in todos" :key="todo.id">
          <todo :todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
      </div>
  </div>
</template>

<script>
import todo from "./todo"
export default {
    name: "todos",
    components:{
        todo
    },
    props: ["todos"]
}
</script>

<style>

</style>