<template>
  <div class="posts row">
      <div class="col-sm-4 mb-2" v-for="post in posts" :key="post.id">
          <post :post="post"/>
      </div>
  </div>
</template>

<script>
import post from "./Post"
export default {
    name: "posts",
    components:{
        post
    },
    props: ["posts"]
}
</script>

<style>

</style>