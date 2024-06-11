<script setup>
import { reactive } from "vue";
import TodoButton from "./TodoButton.vue";

const todoState = reactive({
  todo: "",
  invalid: null,
  errMsg: "",
});

const emit = defineEmits(["create-todo"]);

const createTodo = () => {
  todoState.invalid = null;
  if (todoState.todo !== "") {
    emit("create-todo", todoState.todo);
    todoState.todo = "";
    return;
  }
  todoState.invalid = true;
  todoState.errMsg = "Todo value cannot be empty";
};
</script>

<template>
  <div class="input-wrap" :class="{ 'input-err': todoState.invalid }">
    <input type="text" v-model="todoState.todo" @keydown.enter="createTodo" />
    <TodoButton @click="createTodo" />
  </div>
  <p v-show="todoState.invalid" class="err-msg text">{{ todoState.errMsg }}</p>
</template>

<style lang="scss" scoped>
.input-wrap {
  display: flex;
  transition: 250ms ease;
  border-radius: 8px;
  padding: 20px;
  background-image: linear-gradient(
    rgba(4, 19, 156, 0.5),
    rgba(5, 235, 228, 0.5)
  );

  &.input-err {
    border-color: red;
  }

  &:focus-within {
    box-shadow:
      0 -4px 6px -1px rgb(0 0 0 / 0.1),
      0 -2px 4px -2px rgb(0 0 0 / 0.1);
  }

  input {
    width: 100%;
    padding: 8px 6px;
    border: none;
    background-image: linear-gradient(
      rgba(4, 19, 156, 0.5),
      rgba(5, 235, 228, 0.5)
    );

    &:focus {
      outline: none;
    }
  }
}

.err-msg {
  margin-top: 6px;
  font-size: 12px;
  text-align: center;
  color: red;
}
</style>
