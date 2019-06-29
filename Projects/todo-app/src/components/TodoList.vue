<template>
  <div class="todo-list">
    <transition-group name="list" tag="ul">
      <li
        v-for="(todoItem, index) in todoItems"
        :key="`${todoItem}-${index}`">
        <i
          class="check-icon fas fa-check"
          aria-hidden="true" />
        {{ todoItem }}
        <i
          class="remove-button far fa-trash-alt"
          aria-hidden="true"
          @click="removeTodo(todoItem, index)" />
      </li>
    </transition-group>
  </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'

export default {
  name: 'TodoList',
  computed: {
    ...mapState(['todoItems']),
  },
  methods: {
    ...mapActions({
      storeRemoveTodo: 'removeTodo',
    }),
    removeTodo(todoItem, index) {
      this.storeRemoveTodo({ todoItem, index })
    }
  }
}
</script>

<style lang="scss" scoped>
ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

li {
  padding: 16px;
  background-color: white;
  border-radius: 5px;
  display: flex;
  align-items: center;

  & + & {
    margin-top: 8px;
  }
}

.check-icon {
  color: #62acde;
  margin-right: 4px;
}

.remove-button {
  margin-left: auto;
  color: #de4343;
}

.list-enter-active,
.list-leave-active {
  transition: all 0.5s;
}

.list-enter,
.list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
</style>
