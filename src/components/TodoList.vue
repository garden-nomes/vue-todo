<template>
  <div class="todo-list">
    <ul>
      <TodoItem
        v-for="todo in (hideCompleted ? activeTodos : sortedTodos)"
        :key="todo.id"
        :todo="todo"
        @delete="$emit('deleteTodo', $event)"
      />
    </ul>
    <button type="button" v-if="hideCompleted" @click="hideCompleted = false">
      show completed
    </button>
    <button type="button" v-else @click="hideCompleted = true">
      hide completed
    </button>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
  name: "TodoList",
  components: { TodoItem },
  props: {
    todos: Array
  },
  data() {
    return {
      hideCompleted: false
    };
  },
  computed: {
    sortedTodos() {
      return this.todos.slice(0).sort((a, b) => {
        if (a.done && !b.done) {
          return 1;
        } else if (!a.done && b.done) {
          return -1;
        } else {
          return b.createdAt - a.createdAt;
        }
      });
    },
    activeTodos() {
      return this.sortedTodos.filter(todo => !todo.done);
    }
  }
};
</script>

<style scoped>
.todo-list ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

.todo-list button {
  /* reset */
  border: none;
  margin: 0;
  padding: 0;
  width: auto;
  overflow: visible;
  background: transparent;
  color: inherit;
  font: inherit;
  line-height: normal;
  -webkit-font-smoothing: inherit;
  -moz-osx-font-smoothing: inherit;
  -webkit-appearance: none;

  line-height: 1.75rem;
  width: 100%;
  cursor: pointer;
  font-size: 0.9rem;
  border-bottom-left-radius: 0.25rem;
  border-bottom-right-radius: 0.25rem;
}

.todo-list button::-moz-focus-inner {
    border: 0;
    padding: 0;
}

.todo-list button:hover {
  background: #f7f7f7;
}
</style>
