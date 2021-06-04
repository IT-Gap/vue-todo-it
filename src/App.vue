<template>
  <div id="app" class="d-flex justify-content-center align-items-center">
    <main-card class="position-relative p-4 rounded">
      <date />

      <add-todo
        @add-new-todo="add_todo"
        class="d-flex flex-nowrap flex-row mt-4"
      />

      <todo-counter :number-of-todos="todos.length" class="todo-counter" />

      <todo-card
        v-for="(todo, index) in todos"
        :key="index"
        :todo="todo"
        @checked="checking"
        class="todo-card p-2 mb-2 rounded-3"
      />

      <button
        @click="clear_all()"
        class="clear-btn mb-1  border-0 p-2 rounded-3"
      >
        Clear All
      </button>
    </main-card>
  </div>
</template>

<script>
import Date from "./components/Date";
import TodoCounter from "./components/TodoCounter";
import MainCard from "./components/MainCard";
import TodoCard from "./components/TodoCard";
import AddTodo from "./components/AddTodo";

export default {
  name: "App",
  components: { AddTodo, TodoCard, MainCard, TodoCounter, Date },
  data: () => ({
    todos: [
      {
        name: "todo-test",
        checked: false,
        id: 0
      }
    ]
  }),

  methods: {
    checking(id) {
      let index = this.todos.findIndex(todo => todo.id === id);
      this.todos[index].checked = !this.todos[index].checked;
    },

    add_todo(name) {
      this.todos.push({ name, checked: false, id: this.todos.length });
    },

    clear_all() {
      this.todos = [];
    }
  }
};
</script>

<style lang="sass">
@import "src/assets/style.sass"
</style>
