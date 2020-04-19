<template>
  <div>
    <form @submit="creatingtodo" class="form">
         <div class="form-group">
            <input v-model="input" type="text" class="form-control mr-2" placeholder="Add Todo....">
            <button v-on:submit="$emit('newtodo', id)" type="submit" class="btn btn-primary">Add</button>
        </div>
    </form>
  </div>
</template>

<script>
export default {
    name: "addtodo",
    props: ["todos"],
    data(){
        return{
            input : ""
        }
    },
    methods:{
        creatingtodo(e){
            e.preventDefault();
            var newtodo = {
                id: this.todos.length + 1,
                title: this.input,
                completed: false
            }
            this.input = "";
            this.$emit("add-todo", newtodo)
        }
    }
}
</script>

<style>
.form-group{
    display: flex;
}
input[type="text"]{
    flex: 10;
}
button{
    flex: 2;
}
</style>