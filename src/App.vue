<template>
  <div id="app">
    <TodoList :todos='todos' @deleteTodo='deleteTodo' />
    <AddTodo @submit='addTodo' />
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
