<template>
  <div>
    <todo-header />
    <todo-input />
    <todo-list />
    <todo-footer />
  </div>
</template>

<script>
import { mapActions } from 'vuex'

import TodoHeader from './components/TodoHeader'
import TodoInput from './components/TodoInput'
import TodoList from './components/TodoList'
import TodoFooter from './components/TodoFooter'

export default {
  name: 'app',
  components: {
    TodoHeader,
    TodoInput,
    TodoList,
    TodoFooter,
  },
  created() {
    if (localStorage.length > 0) {
      for (let index = 0; index < localStorage.length; index++) {
        this.addTodo(localStorage.key(index))
      }
    }
  },
  methods: {
    ...mapActions(['addTodo']),
  }
}
</script>

<style lang="scss">
body {
  background-color: #f6f5f8;
}

* {
  box-sizing: border-box;
}

.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>

<style lang="scss" scoped>
.todo-header {
  margin-top: 40px;
  margin-bottom: 24px;
}

.todo-list {
  margin-top: 16px;
  margin-bottom: 16px;
}
</style>
