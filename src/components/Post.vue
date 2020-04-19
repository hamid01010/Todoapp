<template>
  <div>
        <div class="card mx-auto">
            <div class="card-body">
            <h4 class="card-title">{{post.title.substring(0, 30)}}</h4>
            <p class="card-text">{{post.body.substring(0, 90) + "..."}}</p>
        </div>
</div>
  </div>
</template>

<script>
export default {
    name: "post",
    props:["post"]
}
</script>

<style>

</style>