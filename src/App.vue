<script>
export default {
  data() {
    return{
      newTask: "",
      todos: [
        {
          done: false,
          text:"Do something"
        }
      ]
    }
  },
  methods: {
    addTodo() {
      if(this.newTask == "") {
        return
      }

        const todo = {
        done: false,
        text: this.newTask
      }
      this.todos.push(todo)
      this.newTask = ""
    }
  }
}
</script>

<template>
<h1>My ToDo's</h1>
<br>
<div v-for="todo in todos" :key="todo.text">
  <input type="checkbox" v-model="todo.done">
  <span>{{todo.text}}</span>
  <button>Edit</button>
  <button>Delete</button>
</div>

<label for="add-todo">Add a Todo</label>
<input type="text" id="add-todo" v-model="newTask">
<button @click="addTodo">Add</button>
</template>

<style>

</style>
