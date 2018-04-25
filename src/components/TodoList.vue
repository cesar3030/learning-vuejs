<template>
 <div class='container'>
  <h1>{{ name }}</h1>
  <div class='row'>
    <form @submit.prevent="addTodo">
      <input type="text" v-model="todo"/>
      <select v-model="severity">
        <option value="" disabled>Choose Severity</option>
        <option value="high">High</option>
        <option value="medium">Medium</option>
        <option value="low">Low</option>
      </select>
      <p>Adding: {{ todo }} -> {{ severity }}</p> 
    </form>
  </div>
  <div class='row'>
    <ul id="todoList">
      <li v-bind:class="data.severity" v-for="(data, index) in todos" :key="index">{{ index }}: {{ data.title }} <i class="material-icons" v-on:click="deleteTodo(index)">delete</i></li>
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
        {title: 'Bring wetsuit', severity: 'low'},
        {title: 'Sim Card', severity: 'medium'},
        {title: 'Passport', severity: 'high'},
      ],
      todo: '',
      severity: ''
    }
  },
  methods: {
    addTodo() {
      console.log(this.todo)
      this.todos.push({ title: this.todo, severity: this.severity })
      this.todo = ''
      this.severity = ''
    },
    deleteTodo(index){
      this.todos.splice(index,1)
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
  padding: 15px 0px 40px;
}

#todoList {
  width: 85%;
}

#todoList > li, i {
  line-height: 43px;
}

#todoList > li{
  text-align: left;
  display: block;
  -webkit-border-radius: 4px;
  -moz-border-radius: 4px;
  border-radius: 4px;
  height: 40px;
  margin-top: 10px;
  padding: 10px;
  width: 100%;
}

#todoList > li.low {
  background-color: #ffff0259;
}

#todoList > li.medium{
  background-color: #ffa5024a;
}

#todoList > li.high {
  background-color: #ff000042;
}

#todoList > li > i {
  float: right;
  cursor: pointer;
}


.row {
  margin-top: 10px;
  width:100%;
}
</style>
