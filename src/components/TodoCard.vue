<template>
  <div>
    <form class="d-flex align-items-center">
      <input
        type="checkbox"
        @click="checkEvent(todo.id)"
        class="form-check-input"
      />
      <label
        class="px-3 "
        :class="todo.checked ? 'text-decoration-line-through' : ''"
      >
        {{ todo.name }}
      </label>
    </form>
  </div>
</template>

<script>
export default {
  props: ["todo"],
  name: "TodoCard",

  methods: {
    checkEvent() {
      this.$emit("checked", this.todo.id);
    }
  }
};
</script>
