<template>
  <div class="todoPage">
    <h1 class="title">ToDo List</h1>
    <div class="todo-content">
      <div class="new-todo">
        <form @submit.prevent="onAddNewTodo()">
          <input v-model="newTodoText" />
          <input type="submit" value="Add" />
        </form>
      </div>

      <div class="todo-list">
        <template v-for="(todo, index) in todos">
          <todo :model="todo" :key="index" @delete="onDeleteItem(index)"></todo>
          <!-- {{todo.text}} - {{todo.completed}} -->
        </template>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "./Todo";

export default {
  name: "TodoPage",
  components: {
    Todo
  },
  data() {
    return {
      todos: [
        {
          text: "The first todo",
          completed: true
        }
      ],
      newTodoText: ""
    };
  },
  methods: {
    onAddNewTodo() {
      this.todos.push({ text: this.newTodoText, completed: false });
      this.newTodoText = "";
    },
    onDeleteItem(itemIndex) {
      this.todos.splice(itemIndex, 1);
    }
  }
};
</script>

<style scoped lang="scss">
$title-color: red;

.todoPage {
  padding: 0.5rem;
}

.title {
  color: $title-color;
}

.todo-list {
  margin-top: 0.5rem;
}
</style>
