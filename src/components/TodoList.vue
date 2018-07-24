<template>
  <div>
    <p>
      Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}
    </p>
    <p>
      Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}
    </p>
    <todo-item  v-on:delete-todo="deleteTodo" v-for="(todo, index) in todos" v-bind:todo="todo" v-bind:index="index"></todo-item>
  </div>
</template>

<script>
import TodoItem from './TodoItem'
export default {
  name: 'TodoList',
  components: {
    TodoItem
  },

  methods: {
    deleteTodo(index) {
      this.todos.splice(index, 1);
    }
  },
  data () {
    return {
      todos: [{
        title: 'Todo A',
        project: 'Project A',
        done: false
      }, {
        title: 'Todo B',
        project: 'Project B',
        done: true
      }, {
        title: 'Todo C',
        project: 'Project C',
        done: false
      }, {
        title: 'Todo D',
        project: 'Project D',
        done: false
      }]
    }
  }
}
</script>

<style></style>
