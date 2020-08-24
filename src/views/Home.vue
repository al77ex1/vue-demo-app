<template>
  <div>
    <h2>Home page</h2>
    <div
      class="desc"
    >Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</div>
    <router-link to="/todos" class="btn">Todos</router-link>
  </div>
</template>

<style scoped lang="scss">
.desc {
  background: rgba(0, 0, 0, 0.2);
  padding: 1rem;
  color: white;
  text-align: left;
  margin-bottom: 1rem;
}
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