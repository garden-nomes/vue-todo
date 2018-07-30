<template>
  <div id="app">
    <AddTodo @submit='addTodo' />
    <TodoList :todos='todos' @deleteTodo='deleteTodo' />
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";
import AddTodo from "./components/AddTodo.vue";

export default {
  name: "app",
  components: { TodoList, AddTodo },
  data: function() {
    return {
      todos: [
        {
          id: 0,
          name: "Ease the sheets",
          done: true,
          createdAt: new Date()
        },
        {
          id: 1,
          name: "Mizzen to weather",
          done: false,
          createdAt: new Date()
        },
        {
          id: 2,
          name: "Mains'l haul",
          done: false,
          createdAt: new Date()
        }
      ],
      currentTodoId: 3
    };
  },
  methods: {
    addTodo(name) {
      this.todos.push({
        id: this.currentTodoId,
        name,
        done: false,
        createdAt: new Date()
      });

      this.currentTodoId++;
    },
    deleteTodo(id) {
      const index = this.todos.findIndex(todo => todo.id === id);
      this.todos.splice(index, 1);
    }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Roboto:400,900");

body {
  background: #f7f7f7;
}

#app {
  max-width: 25rem;
  margin: 2rem auto;
  background: #fff;
  border-radius: 0.25rem;
  border: 0.0625rem solid #999;
  font-family: "Roboto", sans-serif;
  box-shadow: 0px 0px 5px 0px rgba(0, 0, 0, 0.1);
}

#app h1 {
  margin: 0;
  text-align: center;
}
</style>
