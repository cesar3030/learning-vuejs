<template>
 <div class='container'>
  <h1>{{ name }}</h1>
  <div class='row'></div>
  <div class='row'>
    <ul id="todoList">
      <li v-for="(data, index) in todos" :key="index"> {{ index }}: {{ data.title }}</li>
    </ul>
  </div>
 </div>
</template>

<script>
export default {
  name: 'TodoList',
  props: {
    name: String
  },
  data() {
    return {
      todos:[
        {title: 'Bring wetsuit', severity: 3},
        {title: 'Sim Card', severity: 2},
        {title: 'Passport', severity: 1},
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  width: 50%;
  margin: auto;
  background-color: #f3f3f3;
  min-height: 400px;
  padding-top: 15px;
}

#todoList {
  float: left;
}
#todoList > li{
  text-align: left;
  display: block;
}

.row {
  margin-top: 10px;
  width:100%;
}
</style>
