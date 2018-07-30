<template>
  <form
    id="add-todo"
    @submit="onSubmit"
  >
    <input v-model="name" />
    <button type="submit">submit</button>
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
