<template>
  <div>
    <h2>Todo List</h2>
    <router-link to="/" class="btn">Home</router-link>
    <hr />
    <AddTodo @add-todo="addTodo" />
    <hr />
    <Loader v-if="loading" />
    <TodoList v-else-if="todos.length" v-bind:todos="todos" @remove-todo="removeTodo" />
    <p v-else>No todos!</p>
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddTodo from "@/components/AddTodo";
import Loader from "@/components/Loader";

export default {
  name: "App",
  data() {
    return {
      todos: [],
      loading: true,
    };
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=3")
      .then((response) => response.json())
      .then((json) => {
        this.todos = json;
        this.loading = false;
      });
  },
  components: {
    TodoList,
    AddTodo,
    Loader,
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((t) => t.id !== id);
    },
    addTodo(todo) {
      this.todos.push(todo);
    },
  },
};
</script>

<style scoped lang="scss">
.btn {
  color: white;
  text-decoration: none;
  background-color: #36495d;
  padding: 1rem;
  text-transform: uppercase;
  display: inline-block;
  transition: 0.3s;
  &:hover {
    background-color: lighten(#36495d, 10%);
  }
}
</style>