<template>
  <li :class="{ 'todo-item': true, 'todo-item_done': todo.done }">
    <template v-if="editing">
      <input v-model="todo.name" />
      <button type="submit" @click="editing = false">done</button>
    </template>

    <template v-else>
      <div @click='todo.done = !todo.done' class="todo-item--name">
        {{ todo.name }}
      </div>

      <button type="button" @click="editing = true">
        edit
      </button>
      <button type="button" @click="$emit('delete', todo.id)">
        delete
      </button>
    </template>
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
.todo-item {
  border-top: .0625rem solid #999;
  line-height: 2.5rem;
  cursor: pointer;

  display: flex;
  justify-content: space-between;
}

.todo-item--name {
  padding-left: 0.5rem;
  flex: 1
}

.todo-item--name:hover {
  background: #f7f7f7;
}

.todo-item:last-of-type {
  border-bottom: 0.0625rem solid #999;
}

.todo-item_done {
  color: #999;
}

.todo-item_done .todo-item--name {
  text-decoration: line-through;
}

.todo-item button {
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

  border-left: .0625rem solid #999;
  line-height: 2.5rem;
  padding: 0 0.5rem;
  cursor: pointer;
}

.todo-item button:hover {
  background: #f7f7f7;
}

.todo-item button::-moz-focus-inner {
    border: 0;
    padding: 0;
}

.todo-item input {
  border: none;
  padding: 0 0.5rem;
  flex: 1;
  font-size: 1rem;
}
</style>
