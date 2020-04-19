<template>
  <div>
    <p :class="{isComplete:todo.completed}">
        <input v-on:change="toggleStatus" type="checkbox">
          {{todo.title}}
        <button @click="$emit('del-todo', todo.id)" class="btn btn-danger">delete</button>
    </p>
  </div>
</template>

<script>
export default {
    name: "todo",
    props: ["todo"],
    methods:{
        toggleStatus(){
            this.todo.completed = !this.todo.completed            
        }
    }
}
</script>

<style scoped>
button{
    float: right
}
.isComplete{
    text-decoration: line-through;
}
p{
    background: #6c757d52;
    font-size:18px;
    line-height: 38px;
    border-radius: 5px;
    padding: 8px;
}
</style>
