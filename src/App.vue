<script>
export default {
  data() {
    return{
      newTask: "",
      todos: [
        {
          done: false,
          text:"Do something",
          edit: false
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
        text: this.newTask,
        edit: false
      }
      this.todos.push(todo)
      this.newTask = ""
    },
    deleteTodo(index){
      this.todos.splice(index, 1)
    }
  }
}
</script>

<template>

<h1>My ToDo's</h1>

<br>

<div v-for="(todo, index) in todos" :key="todo.text">

  <input type="checkbox" v-model="todo.done">

  <span v-if="!todo.edit">{{todo.text}}</span>
  <input type="text" :value="todo.text" @blur="todo.text = $event.target.value; todo.edit = false" v-if="todo.edit">

  <button @click="todo.edit = !todo.edit">Edit</button>
  <button @click="deleteTodo(index)">Delete</button>

</div>

<label for="add-todo">Add a Todo</label>
<input type="text" id="add-todo" v-model="newTask">
<button @click="addTodo">Add</button>
</template>

<style>

</style>
