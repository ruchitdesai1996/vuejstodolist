<template>
  <div class="todo-item" v-bind:class="{ 'is-completed': todoLocal.completed }">
    <p>
      <input type= "checkbox" v-on:change= "markComplete" />
      {{ todo.title }}
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  data() {
    return {
      todoLocal: this.todo,
    };
  },
  methods: {
    markComplete() {
      this.todoLocal.completed = !this.todoLocal.completed;
    },
  },
};
</script>

<style scoped>
    .todo-item {
        background-color: gray;
        font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
        padding:5px;
        border-bottom: 1cm;
        border-bottom-color: black;
        text-align: left;
    }

    .is-complete {
        text-decoration: line-through;   
        }

    .del {
        shape-margin:2cm;
        background:red;
        color:black;
        shape-margin: 2cm;
    }
</style>