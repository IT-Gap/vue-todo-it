<template>
  <div class="todo-counter">
    <p>You have {{ numberOfTodos }} todos left</p>
  </div>
</template>

<script>
export default {
  props: ["numberOfTodos"],
  name: "TodoCounter"
};
</script>

<style scoped></style>
