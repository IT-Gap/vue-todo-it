<template>
  <div id="app">
    <div class="main-card">
      <!--  date   -->
      <div class="date">
        <h3>
          {{ day() }} <br />
          {{ date() }}
        </h3>
        dsajbdmbsadb
      </div>

      <!--   todo-text-input ,todo-add-btn    -->
      <div class="add-todo">
        <input @keyup.enter="add_todo()" type="text" v-model="name" />
        <button @click="add_todo()">+</button>
      </div>

      <!--   todo-counter    -->
      <div class="todo-counter">
        <p>You have {{ todos.length }} todos left</p>
      </div>

      <!--   todo-cards    -->
      <div class="todo-card" v-for="(todo, index) in todos" :key="index">
        <form>
          <input
            type="checkbox"
            @click="checking(index)"
            :checked="todo.checked"
          />
          <label :class="todo.checked ? 'done' : ''">
            {{ todo.name }}
          </label>
        </form>
      </div>

      <!--   show-complete-btn, clear-all-btn    -->
      <div class="buttons">
        <button @click="clear_all()">
          Clear All
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import moment from "moment";

export default {
  name: "App",
  data: () => ({
    number_of_todos: 5,
    todos: [
      {
        name: "todo-test",
        checked: false
      }
    ],

    name: ""
  }),

  methods: {
    checking(index) {
      this.todos[index].checked = !this.todos[index].checked;
    },

    add_todo() {
      this.todos.push({ name: this.name, checked: false });
      this.name = "";
    },

    clear_all() {
      this.todos = [];
    },

    day() {
      return moment().format("dddd");
    },

    date() {
      return moment().format("MMM DD Y");
    }
  }
};
</script>

<style lang="sass">
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;600;700&display=swap')
$primary: #00d87f

.todo-card
  padding: 8px
  border-radius: 4px
  background-color: #fff
  box-shadow: gray 1px 1px 2px
  margin-bottom: 8px



.buttons
  bottom: 0
  position: absolute
  display: flex
  justify-content: space-around
  width: 100%
  bottom: 0
  left: 0
  button
    border: none
    padding: 8px
    margin: 0 0 20px
    border-radius: 4px
    background-color: #f0f0f0
    transition: all 0.5s
    &:hover
      background-color: #e5e5e5


.done
  text-decoration: line-through


body
  margin: 0
  padding: 0
  box-sizing: border-box
  font-family: 'Open Sans', sans-serif !important

#app
  width: 100vw
  height: 100vh
  display: flex
  align-items: center
  justify-content: center
  background: linear-gradient(-20deg, #1d976c, #93f9b9)
  background: -webkit-linear-gradient(-20deg, #1d976c, #93f9b9)

.main-card
  padding: 24px
  min-width: 400px
  min-height: 500px
  border-radius: 4px
  position: relative
  background-color: #FFF
  box-shadow: gray 2px 2px 4px


.date
  h3
    color: $primary
    font-weight: 400

.add-todo
  display: flex
  flex-wrap: nowrap
  flex-direction: row
  button
    border: none
    color: $primary
    font-size: 24px
    padding: 0px 16px
    border-radius: 4px
    background: #fefefe
    transition: all 0.5s
    &:hover
      background-color: #e5e5e5

  input
    width: 100%
    padding: 4px
    border: none
    border-radius: 2px
    margin-right: 10px
    background-color: #fff
    border-bottom: 1px solid $primary
    &:focus
      outline: none
      border-radius: 2px
      caret-color: $primary
      //border: 1px solid $primary
</style>
