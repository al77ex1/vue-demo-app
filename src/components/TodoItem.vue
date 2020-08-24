<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox" v-on:change="todo.completed = !todo.completed" />
      <strong>{{ index + 1 }}</strong>
      {{ todo.title }}
    </span>
    <button class="rm" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    index: Number,
  },
};
</script>

<style scoped lang="scss">
ul {
  li {
    border-bottom: 1px solid white;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 1rem;
    &:first-child {
      padding-top: 0;
    }
  }
}
input {
  margin-right: 1rem;
}
.rm {
  border: none;
  background: #de4547;
  color: white;
  border-radius: 50%;
  outline: none;
  font-size: 2rem;
  width: 2.44rem;
  cursor: pointer;
  transition: 0.3s;
  &:hover {
    background-color: lighten(#de4547, 10%);
  }
}
.done {
  text-decoration: line-through;
}
</style>
