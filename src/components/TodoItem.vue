<template>
  <div class='ui centered card' >
    <div class='content' v-show='!isEditing'>
      <div class='header'>
        {{ todo.title }}
      </div>
      <div class='meta'>
        {{ todo.note }}
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
            Note
          </label>
          <input type="text" v-model="todo.note">
        </div>
        <div class='ui two button attached buttons'>
          <button class='ui basic basic button' v-on:click='hideForm'>
            Close X
          </button>
        </div>
      </div>
    </div>

    <button class='ui buttom attached green basic button' v-show='!isEditing && todo.done' v-on:click='completeTodo(index)'>
      Completed
    </button>
    <button class='ui buttom attached red basic button' v-show='!isEditing && !todo.done' v-on:click='completeTodo(index)'>
      Pending
    </button>
  </div>
</template>

<script>
export default {
  props: ['todo', 'index'],
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
    },
    completeTodo(index){
      this.$emit('complete-todo', index);
    }
  }
}
</script>

<style>

</style>
