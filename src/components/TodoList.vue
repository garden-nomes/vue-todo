<template>
  <div class="todo-list">
    <button type="button" v-if="hideCompleted" @click="hideCompleted = false">
      show completed
    </button>
    <button type="button" v-else @click="hideCompleted = true">
      hide completed
    </button>
    <ul>
      <TodoItem
        v-for="todo in (hideCompleted ? activeTodos : sortedTodos)"
        :key="todo.id"
        :todo="todo"
        @delete="$emit('deleteTodo', $event)"
      />
    </ul>
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
