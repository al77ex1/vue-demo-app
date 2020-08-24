<template>
  <form @submit.prevent="onSubmit">
    <input class="add" type="text" v-model="title" />
    <button type="submit">Create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: "",
    };
  },
  methods: {
    onSubmit() {
      console.log("submit", this.title);
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false,
        };
        this.$emit("add-todo", newTodo);
        this.title = "";
      }
    },
  },
};
</script>

<style scope lang="scss">
form {
  display: flex;
}
input.add {
  width: 400px;
}
form {
  padding: 1rem;
  margin: 1rem 0;
  background: rgba(0, 0, 0, 0.2);
  input {
    border: none;
    background-color: rgba(255, 255, 255, 0.9);
    padding: 0.8rem;
    &:focus {
      outline: none;
    }
  }
  button {
    color: white;
    background-color: #36495d;
    text-transform: uppercase;
    transition: 0.3s;
    border: none;
    cursor: pointer;
    outline: none;
    padding: 0 1rem;
    &:hover {
      background-color: lighten(#36495d, 10%);
    }
  }
}
</style>
