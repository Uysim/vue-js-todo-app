<template>
  <div class='ui centered card' >
    <div class='content' v-show='!isEditing'>
      <div class='header'>
        {{ todo.title }}
      </div>
      <div class='meta'>
        {{ todo.project }}
      </div>
      <div class='extra content'>
        <a class='right floated trash icon' v-on:click='deleteTodo(index)'>
          <i class='trash red icon'></i>
        </a>
        <a class='right floated edit icon' v-on:click='showForm'>
          <i class='edit icon'></i>
        </a>

      </div>
    </div>

    <div class='content' v-show='isEditing'>
      <div class='ui form'>
        <div class='field'>
          <label>
            Title
          </label>
          <input type="text" v-model="todo.title">
        </div>
        <div class='field'>
          <label>
            Project
          </label>
          <input type="text" v-model="todo.project">
        </div>
        <div class='ui two button attached buttons'>
          <button class='ui basic blue button' v-on:click='hideForm'>
            Close X
          </button>
        </div>
      </div>
    </div>

    <div class='ui buttom attached green basic button' v-show='!isEditing && todo.done'>
      Completed
    </div>
    <div class='ui buttom attached red basic button' v-show='!isEditing && !todo.done'>
      Pending
    </div>
  </div>
</template>

<script>
export default {
  props: ['todo'],
  data () {
    return {
      isEditing: false
    }
  },
  methods: {
    deleteTodo (index) {
      this.$emit('delete-todo', index)
    },
    showForm () {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    }
  }
}
</script>

<style>

</style>
