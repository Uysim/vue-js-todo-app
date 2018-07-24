<template>
  <div class='ui centered card' >
    <div class='content'>
      <div class='ui form'>
        <div class='field'>
          <label>
            Title
          </label>
          <input type="text" v-model="todo.title">
        </div>
        <div class='field'>
          <label>
            Note
          </label>
          <input type="text" v-model="todo.note">
        </div>
      </div>
    </div>
    <button class='ui buttom attached primary basic button' v-on:click="addItem">
      Add
    </button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      todo: {}
    }
  },
  methods: {
    addItem () {
      this.$emit('add-todo', this.todo);
      this.todo = {};
    }
  }
};
</script>

<style>
</style>
