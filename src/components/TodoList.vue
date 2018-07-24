<template>
  <div class='ui internally celled grid'>
    <div class='row'>
      <div class="three wide column">
        <p>
        Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}
        </p>
        <p>
          Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}
        </p>

        <new-todo v-on:add-todo="addTodo"></new-todo>
      </div>

      <div class="thirteen wide column">
        <todo-item  v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="(todo, index) in todos" v-bind:todo="todo" v-bind:index="index"></todo-item>

      </div>
    </div>
  </div>
</template>

<script>
import TodoItem from './TodoItem'
import NewTodo from './NewTodo'
export default {
  name: 'TodoList',
  components: {
    TodoItem,
    NewTodo
  },

  methods: {
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
    addTodo(item){
      this.todos.push({...item, done: false});
    },
    completeTodo(index){
      console.log(index);
      console.log(this.todos);
      this.todos[index].done = true
    }
  },
  data () {
    return {
      todos: [{
        title: 'Todo A',
        note: 'Note A',
        done: false
      }, {
        title: 'Todo B',
        note: 'Note B',
        done: true
      }, {
        title: 'Todo C',
        note: 'Note C',
        done: false
      }, {
        title: 'Todo D',
        note: 'Note D',
        done: false
      }]
    }
  }
}
</script>

<style></style>
