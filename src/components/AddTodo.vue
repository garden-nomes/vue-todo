<template>
  <form
    id="add-todo"
    @submit="onSubmit"
  >
    <input v-model="name" placeholder="Add todo..." />
    <button type="submit">
      <font-awesome-icon icon="plus" fixed-width />
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      name: ""
    };
  },
  methods: {
    onSubmit(event) {
      this.$emit("submit", this.name);
      this.name = "";
      event.preventDefault();
    }
  }
};
</script>

<style scoped>
#add-todo {
  display: flex;
  line-height: 2.5;
  border-top-left-radius: 0.25rem;
  border-top-right-radius: 0.25rem;
}

input {
  line-height: 2.5;
  font-size: 0.9rem;
  padding: 0 0.5rem;
  border: none;
  flex: 1;
  background: none;
  border-top-left-radius: 0.25rem;
}

button {
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

  border-left: 0.0625rem solid #999;
  border-top-right-radius: 0.25rem;
  line-height: 2.5;
  padding: 0 0.5rem;
  cursor: pointer;
}

button:hover {
  background: #f7f7f7;
}

.todo-item button::-moz-focus-inner {
  border: 0;
  padding: 0;
}
</style>
