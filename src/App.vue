<template>
  <div id="app">
    <ul>
      <li v-for="(todo, index) in this.todos" :key = index><span>{{todo.name}}</span>
      <span :class = "urgent" v-if="todo.priority === 'high'"> URGENT </span></li>
    </ul>
    <form v-on:submit.prevent="addNewTodo">
      <label for="new-todo">Add New To-Do</label>
      <input type="text" id="new-todo" v-model="newTodo"/>
      <label for="high"> High </label>
      <input type="radio" id="high" name="priority" value="high" v-model="newTodoPriority"/>
      <label for="low"> Low </label>
      <input type="radio" id="low" name="priority" value="low" v-model="newTodoPriority"/>
      <input type="submit" value="Add New To-Do"/>
    </form>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
    todos: [{name: "Wash Car", priority: "low"},
    {name: "Cook Dinner", priority: "high"},
    {name: "Walk Dog", priority: "high"}
    ],
    newTodo: "",
    newTodoPriority: ""
    }
  },
  methods: {
    addNewTodo: function(){
      this.todos.push({name: this.newTodo, priority: this.newTodoPriority});
      newTodo = ""
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
li {
  border: 2px black;
  color: green;
  padding: 10px
}

.urgent {
  

}
</style>
