<template>
  <div class="add-todo">
    <input
      class="p-1 me-3"
      @keyup.enter="add_todo()"
      type="text"
      v-model="todo_name"
    />
    <button class="rounded border-0 px-3" @click="add_todo()">+</button>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data: () => ({
    todo_name: ""
  }),

  methods: {
    add_todo() {
      this.$emit("add-new-todo", this.todo_name);
      this.todo_name = "";
    }
  }
};
</script>
