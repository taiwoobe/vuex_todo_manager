<template>
  <div>
      <h3>Todos</h3>
      <div class="legend">
          <span>Double click to mark as completed </span>
          <span>
              <span class="incomplete-box"></span> = Incomplete
          </span>
          <span>
              <span class="complete-box"></span> = Complete
          </span>
      </div>
      <div class="todos">
          <div class="todo" v-for="todo in allTodos" :key="todo.id" @dblclick="onDblClick(todo)" :class="{'is-complete': todo.completed}">
              {{ todo.title }}
              <i class="fas fa-trash-alt" @click="deleteTodo(todo.id)"></i>
          </div>
      </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
export default {
    name: 'Todos',
    computed: mapGetters(['allTodos']),
    created() {
        this.getTodos();
    },
    methods: {
        ...mapActions(['getTodos', 'deleteTodo', 'updateTodo']),
        onDblClick(todo) {
            const updatedTodo = {
                id: todo.id,
                title: todo.title,
                completed: !todo.completed
            }
            this.updateTodo(updatedTodo);
        }
    },
}
</script>

<style lang="scss" scoped>
    .legend {
        display: flex;
        justify-content: space-between;
        margin-bottom: 1rem;
        .complete-box {
            display: inline-block;
            width: 10px;
            height: 10px;
            background: #35495e;
        }
        .incomplete-box {
            display: inline-block;
            width: 10px;
            height: 10px;
            background: #41b883;
        }
    }
    .todos {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
        grid-gap: 1rem;
        .todo {
            border: 1px solid #ccc;
            background: #41b883;
            padding: 1rem;
            border-radius: 5px;
            text-align: center;
            position: relative;
            cursor: pointer;
        }
        i {
            position: absolute;
            bottom: 10px;
            right: 10px;
            color: #fff;
            cursor: pointer;
        }
        .is-complete {
            background: #35495e;
            color: #fff;
        }
    }
</style>