<template>
  <main id="app">
    <h3>{{title}}</h3>
    <form @submit.prevent="addTodo">
      <label for="newTodo">New Todo</label>
      <input v-model="newTodo" type="text" name="newTodo" id="newTodo" value="">
      <button type="submit" name="button">Add</button>
    </form>
    <button @click="allDone" type="button" name="button">All Done</button>
    <ul>
      <li v-for="todo in todos" :key="todo">
        <input type="checkbox" v-model="todo.done">
        <span :class="{ done: todo.done }">{{todo.title}}</span>
        <button @click="removeTodo(todo)" type="button" name="button">Remove</button>
      </li>
    </ul>
  </main>
</template>

<script>
export default {
  name: 'Create',
  data() {
    return{
      title: 'Hello Coding Garden',
      newTodo: '',
      todos: []
    }
  },
  methods : {
    addTodo() {
      this.todos.push({
        title: this.newTodo,
        done: false
      });
      this.newTodo = '';
    },
    removeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    allDone() {
      this.todos.forEach(todo => {
        todo.done = true;
      });
    }
  }
}
</script>
<style>

</style>

