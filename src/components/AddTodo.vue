<template>
  <div>
      <h3>Add Todo</h3>
      <div class="add">
          <form @submit.prevent="onSubmit">
              <input type="text" v-model="title" placeholder="Enter Todo Title">
              <button type="submit"> Submit </button>
          </form>
      </div>
  </div>
</template>

<script>
import { mapActions } from 'vuex'
export default {
    name: 'AddTodo',
    data() {
        return {
            title: ''
        }
    },
    methods: {
        ...mapActions(['addTodo']),
        onSubmit() {
            this.addTodo(this.title);
        }
    },
}
</script>

<style scoped lang="scss">
    form {
        display: flex;
        input {
            flex: 10;
            padding: 10px;
            border: 1px solid #41b883;
            outline: 0;
        }
        button {
            flex: 2;
            background: #41b883;
            color: #fff;
            border: 1px solid #41b883;
            cursor: pointer;
        }
    }
</style>