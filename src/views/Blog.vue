<template>
  <div class="container">
      <h1 class="display-4">Blog</h1>
        <button @click="fetchposts" class="btn btn-secondary col-xs-12"><i class="fa fa-refresh"></i></button>
      <div class="mt-2" v-if="isLoading"><i class="fa fa-spinner fa-spin"></i> Loading...</div>
        <posts v-else v-bind:posts="posts"/>
  </div>
</template>

<script>
import axios from "axios"
import Posts from "../components/Posts"
export default {
    name: "blog",
    components:{
        Posts
    },
    data(){
        return{
            isLoading: true,
            posts : []
        }
    },
    mounted(){
        this.fetchposts()
    },
    methods:{
        change(){
            this.isLoading = !this.isLoading;
        },
        fetchposts(){
            this.isLoading = true;
            axios.get("https://jsonplaceholder.typicode.com/posts")
            .then(res => this.posts = res.data)
            .finally(() => {
                this.isLoading = false
            })
        }
    }
}
</script>

<style>

</style>