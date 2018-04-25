<template>
 <div class='container'>
  <h1>{{ name }}</h1>
  <div class='row'>
    <input type="text" v-model="todo"/>
    <select v-model="severity">
      <option value="" disabled>Choose Severity</option>
      <option value="1">Critical</option>
      <option value="2">Medium</option>
      <option value="3">Low</option>
    </select>
    <p>Adding: {{ todo }} -> {{ severity }}</p> 
    <button v-on:click="addTodo()">Add</button>
  </div>
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
      ],
      todo: '',
      severity: ''
    }
  },
  methods: {
    addTodo() {
      console.log(this.todo)
      this.todos.push({ title: this.todo, severity: 3 })
      this.todo = ''
      this.severity = ''
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
