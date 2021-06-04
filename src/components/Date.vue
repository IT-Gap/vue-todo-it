<template>
  <div class="date">
    <h3>
      {{ day() }} <br />
      {{ date() }}
    </h3>
  </div>
</template>

<script>
import moment from "moment";

export default {
  name: "Date",
  methods: {
    day() {
      return moment().format("dddd");
    },

    date() {
      return moment().format("MMM DD Y");
    }
  }
};
</script>

<style scoped></style>
