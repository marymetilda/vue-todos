<script setup>
import { ref, watch, computed } from "vue";
import { uid } from "uid";
import { Icon } from "@iconify/vue";
import TodoCreator from "@/components/TodoCreator.vue";
import TodoItem from "@/components/TodoItem.vue";
const todoList = ref([]);

watch(
  todoList,
  () => {
    setTodoListLocalStorage();
  },
  { deep: true }
);

const todoCompleted = computed(() => {
  return todoList.value.every((todo) => todo.isCompleted);
});

const fetchTodoList = () => {
  const savedTodoList = JSON.parse(localStorage.getItem("todoList"));
  if (savedTodoList) {
    todoList.value = savedTodoList;
  }
};

fetchTodoList();

const setTodoListLocalStorage = () => {
  localStorage.setItem("todoList", JSON.stringify(todoList.value));
};

const createTodo = (todo) => {
  todoList.value.push({
    id: uid(),
    todo,
    isCompleted: false,
    isEditing: null,
  });
};

const toggleTodoComplete = (todoPos) => {
  todoList.value[todoPos].isCompleted = !todoList.value[todoPos].isCompleted;
};

const toggleEditTodo = (todoPos) => {
  todoList.value[todoPos].isEditing = !todoList.value[todoPos].isEditing;
};

const updateTodo = (todoVal, todoPos) => {
  todoList.value[todoPos].todo = todoVal;
};

const deleteTodo = (todoId) => {
  todoList.value = todoList.value.filter((todo) => todo.id !== todoId);
};
</script>

<template>
  <main>
    <div class="container">
      <h2 class="text">Create Todo</h2>
      <TodoCreator @create-todo="createTodo" />
      <ul class="todo-list" v-if="todoList.length > 0">
        <TodoItem
          v-for="(todo, index) in todoList"
          :todo="todo"
          :index="index"
          @toggle-complete="toggleTodoComplete"
          @delete-todo="deleteTodo"
          @update-todo="updateTodo"
          @edit-todo="toggleEditTodo"
        />
      </ul>
      <p class="todos-msg text" v-else>
        <Icon icon="noto-v1:sad-but-relieved-face" width="22" />
        <span>You have no todo's to complete! Add one!</span>
      </p>
      <p v-if="todoCompleted && todoList.length > 0" class="todos-msg text">
        <Icon icon="noto-v1:party-popper" />
        <span>You have completed all your todos!</span>
      </p>
    </div>
  </main>
</template>

<style lang="scss" scoped>
main {
  width: 100%;
  height: 100%;
  overflow: auto;
}
.container {
  display: flex;
  flex-direction: column;
  max-width: 500px;
  width: 100%;
  height: 100%;
  margin: 0 auto;
  padding: 40px 16px;
  background-color: rgba(2, 2, 2, 0.5);
  margin-top: 16px;
  border-radius: 12px;

  h2 {
    margin-bottom: 16px;
    text-align: center;
    color: #ccc;
  }

  .todo-list {
    display: flex;
    flex-direction: column;
    list-style: none;
    margin-top: 24px;
    gap: 20px;
  }

  .todos-msg {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    margin-top: 24px;
    color: white;
  }
}
@media (max-width: 1024px) {
  h1 {
    font-size: 24px;
  }
}
</style>
