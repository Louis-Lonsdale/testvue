<template>
  <div id="app">
    <h1>To-Do List</h1>
    <ToDoForm @todo-added="addToDo"></ToDoForm>
    <ul>
      <li v-for="item in ToDoItems" :key="item.id">
        <ToDoItem :id="item.id" :label="item.label" :done="item.done"></ToDoItem>
      </li>
    </ul>
  </div>
</template>

<script>
import ToDoItem from './components/ToDoItem.vue';
import ToDoForm from './components/ToDoForm.vue';
import uniqueId from 'lodash.uniqueid';

export default {
  name: 'App',
  components: {
    ToDoItem,
    ToDoForm,
  },
  data()
  {
    return {
      ToDoItems: [
        {id: uniqueId('todo-'), label : 'learn vue', done: false},
        {id: uniqueId('todo-'), label : 'create vue project from the cli', done: false},
        {id: uniqueId('todo-'), label : 'have fun', done: true},
        {id: uniqueId('todo-'), label : 'create to-do list', done: false},
      ],
    };
  },
  methods: {
    addToDo(ToDoLabel) {
      console.log("To-do added: ", ToDoLabel);
      this.ToDoItems.push({id: uniqueId('todo-'), label: ToDoLabel, done: false})
    }
  }

};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
