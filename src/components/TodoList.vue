<template>
 <div class='container'>
 <h1>{{ name }}</h1>
 </div>
</template>

<script>
export default {
  name: 'TodoList',
  props: {
    name: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container{
  width: 50%;
  margin: auto;
  background-color: #f3f3f3
}
</style>
