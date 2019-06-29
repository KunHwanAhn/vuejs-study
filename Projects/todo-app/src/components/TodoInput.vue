<template>
  <div class="todo-input shadow">
    <div class="input-box">
      <input
        ref="todoInput"
        v-model="newTodoItem"
        type="text"
        placeholder="Type what you have to do"
        @keyup.enter="addTodo">
    </div>
    <span
      class="add-btn"
      @click="addTodo">
      <i
        class="fas fa-plus"
        aria-hidden="true" />
    </span>

    <modal v-if="showModal">
      <h3 slot="header">
        경고
      </h3>
      <span
        slot="footer"
        class="close-modal-button"
        @click="showModal = false">
        할 일을 입력하세요.
        <i
          class="fas fa-times"
          aria-hidden="true" />
      </span>
    </modal>
  </div>
</template>

<script>
import { mapActions } from 'vuex'

import Modal from './common/Modal'

export default {
  name: 'TodoInput',
  components: {
    Modal
  },
  data() {
    return {
      newTodoItem: '',
      showModal: false,
    }
  },
  methods: {
    ...mapActions({
      storeAddTodo: 'addTodo',
    }),
    addTodo() {
      if (this.newTodoItem !== '') {
        this.storeAddTodo(this.newTodoItem)
        this.clearTodoItem()
      } else {
        this.showModal = true
      }

      this.$refs.todoInput.focus()
    },
    clearTodoItem() {
      this.newTodoItem = ''
    }
  }
}
</script>

<style lang="scss" scoped>
.todo-input {
  display: flex;
  align-items: center;
}

.input-box {
  flex-grow: 1;
  padding: 16px;
  border-radius: 5px 0 0 5px;
  border-top: 1px solid gray;
  border-bottom: 1px solid gray;
  border-left: 1px solid gray;
  background-color: white;
  display: flex;
  align-items: center;
  justify-content: center;

  input {
    padding: 0;
    width: 100%;
    height: 20px;
    border-style: none;
    font-size: 0.9rem;

    &:focus {
      outline: none;
    }
  }
}

.add-btn {
  border-radius: 0 5px 5px 0;
  border-top: 1px solid gray;
  border-bottom: 1px solid gray;
  border-right: 1px solid gray;
  padding: 17px 20px;
  background: linear-gradient(to right, #6478fb, #8763fb);
  color: white;
  cursor: pointer;

  display: flex;
  align-items: center;
  justify-content: center;

  > i {
    width: 18px;
    height: 18px;
    text-align: center;
  }
}

.close-modal-button {
  cursor: pointer;
}
</style>
