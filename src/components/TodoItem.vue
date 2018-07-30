<template>
  <li :class="{ 'todo-item': true, 'todo-item_done': todo.done }">
    <form v-if="editing" @submit.prevent="editing = false">
      <input v-model="todo.name" />
      <button type="submit">done</button>
    </form>

    <template v-else>
      <span
        class="todo-item--name"
        @click='todo.done = !todo.done'
      >
        {{ todo.name }}
      </span>
    </template>

    <button type="button" v-if="!editing" @click="editing = true">
      edit
    </button>
    <button type="button" v-if="!editing" @click="$emit('delete', todo.id)">
      delete
    </button>
  </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todo: Object
  },
  data() {
    return {
      editing: false
    };
  }
};
</script>

<style scoped>
.todo-item_done {
  opacity: 0.5;
}
.todo-item_done .todo-item--name {
  text-decoration: line-through;
}
</style>
