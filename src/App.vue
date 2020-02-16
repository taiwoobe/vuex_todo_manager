<template>
  <div id="app">
    <div class="container">
      <add-todo/>
      <filter-todo/>
      <todos/>
    </div>
  </div>
</template>

<script>
import AddTodo from './components/AddTodo.vue'
import FilterTodo from './components/FilterTodos.vue'
import Todos from './components/Todos.vue'
export default {
  name: 'App',
  components: {
    AddTodo,
    FilterTodo,
    Todos
  }
}
</script>

<style lang="scss">
body {
  line-height: 1.6;
  background: #e8f7f0;
  .container  {
    max-width: 1100px;
    margin: auto;
    overflow: auto;
    padding: 0 2rem;
  }
}
</style>
