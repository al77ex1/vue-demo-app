<template>
  <div id="app">
    <h1>Todo app</h1>
    <hr />
    <router-view />
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddTodo from "@/components/AddTodo";

export default {
  name: "App",
  data() {
    return {
      todos: [],
    };
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=3")
      .then((response) => response.json())
      .then((json) => {
        this.todos = json;
      });
  },
  components: {
    TodoList,
    AddTodo,
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

<style lang="scss">
html,
body {
  height: 100%;
  display: flex;
  flex-direction: column;
  padding: 0;
  margin: 0;
}
hr {
  border: none;
  background-color: white;
  height: 1px;
}
#app {
  background: linear-gradient(180deg, #299c8b 0%, #ace1d9 100%);
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 1rem;
  height: inherit;
  h1 {
    text-align: left;
    text-transform: uppercase;
  }
}
</style>
