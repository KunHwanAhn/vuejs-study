<template>
  <div class="todo-footer">
    <div
      class="remove-button"
      @click="clearTodoList">
      Clear All Items
    </div>
  </div>
</template>

<script>
export default {
  name: 'TodoFooter',
  methods: {
    clearTodoList() {
      this.$emit('clear-todo-list')
    }
  }
}
</script>

<style lang="scss" scoped>
.todo-footer {
  display: flex;
  align-items: center;
  justify-content: center;
}

.remove-button {
  padding: 16px;
  border-radius: 5px;
  background-color: white;
  color: #e20303;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
