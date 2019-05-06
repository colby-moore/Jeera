<template>
  <div id="app">
    <AddTodoItem v-on:parse-submit="approveItemAdd" />
    <TodoList v-bind:todoList="todoList" v-on:del-items="deleteItems"/>
  </div>
</template>

<script>
import TodoList from '../components/TodoList.vue';
import AddTodoItem from '../components/AddTodoItem';
import axios from 'axios';


export default {
  name: 'Home',
  components: {
    TodoList,
    AddTodoItem
  },
  data() {
    return{
      todoList: [
        // {
        //   id: 1,
        //   title: "Eat Breakfast",
        //   completed: false
        // },
        // {
        //   id: 2,
        //   title: "Eat Lunch",
        //   completed: true
        // },
        // {
        //   id: 3,
        //   title: "Eat Dinner",
        //   completed: false
        // }
      ]
    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(Response => this.todoList = Response.data)
      .catch(err => console.log(err));
  },
  methods: {
    deleteItems(id){
      this.todoList = this.todoList.filter(item => item.id !== id);
    },
    approveItemAdd(newTodoItem){
      const {title, completed } = newTodoItem
      this.todoList = [...this.todoList, newTodoItem];
    },

  }
}
</script>

<style>
 * {
   box-sizing: border-box;
   margin: 0;
   padding: 0;
  }

  body{
    font-family: Arial, Helvetica, sans-serif;
  }

      .modal-open {
        padding-right: 0px !important;
    }

    .modal-input{
        padding: 12px 20px;
        border-radius: 4px;
        background-color:#f4f5f7;
        border: 1px solid #ccc;
        min-height: 150px;
        width: 100%;
    }

    .modal-select {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
    }
</style>
