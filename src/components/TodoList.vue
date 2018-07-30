<template>
  <div class="todo-list">
    <input type="checkbox" v-model="hideCompleted">hide completed</input>
    <ul>
      <TodoItem
        v-for="todo in (hideCompleted ? activeTodos : todos)"
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
      hideCompleted: true
    }
  },
  computed: {
    activeTodos() {
      return this.todos.filter(todo => !todo.done)
    }
  }
};
</script>
