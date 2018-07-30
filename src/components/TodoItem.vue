<template>
  <li :class="{ 'todo-item': true, 'todo-item_done': todo.done }">
    <input v-if="editing" v-model="todo.name" />

    <template v-else>
      <span
        class="todo-item--name"
        @click='todo.done = !todo.done'
      >
        {{ todo.name }}
      </span>
    </template>

    <span class="todo-item--toolbar">
      <a
        class="todo-item--toolbar--button"
        href="#"
        v-if="!editing"
        @click.prevent="editing = true"
      >
        edit
      </a>
      <a
        class="todo-item--toolbar--button"
        href="#"
        v-if="editing"
        @click.prevent="editing = false"
      >
        done
      </a>
      <a
        class="todo-item--toolbar--button"
        href="#"
        @click.prevent="$emit('delete', todo.id)"
      >
        delete
      </a>
    </span>
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
