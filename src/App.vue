<script>
let id = 0

export default {
  data() {
    return {
      newTodo: '',
      todos: []
    }
  },
  
  methods: {
    addTodo() {
      this.todos.push({ id: id++, text: this.newTodo, done: false })
      this.newTodo = ''
    },
    removeTodo(todo) {
      this.todos = this.todos.filter((t) => t !== todo)
    },
    doneTodo (todo) {
   todo.done = !todo.done
    }
  }
}
</script>

<template>
  <input v-model="newTodo" @keyup.enter="addTodo" />
  <button @click="addTodo">Add Todo</button>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <span  :class="{ done: todo.done }" @click="doneTodo(todo)">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
</template>

<style>
.done {
  text-decoration: line-through;
}

button{
   margin-left: 5px;
}


</style>