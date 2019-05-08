<template>
  <div id="app">
    <AddTodoItem v-on:parse-submit="approveItemAdd" />
    <TodoList v-bind:todoList="todoList" v-bind:columnCounters="columnCounters" v-on:del-items="deleteItems"/>
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
    AddTodoItem,
  },
  data() {
    return{
      todoList: [
        {
          id: 1,
          parentColumn: "In Progress",
          title: "MW-1",
          completed: false
        },
        {
          id: 2,
          parentColumn: "In Progress",
          title: "MW-2",
          completed: false
        },
        {
          id: 3,
          parentColumn: "In Progress",
          title: "MW-3",
          completed: false
        },
        {
          id: 4,
          parentColumn: "Ready For Deploy",
          title: "MW-4",
          completed: false
        },
        {
          id: 5,
          parentColumn: "Ready For Deploy",
          title: "MW-5",
          completed: false
        },
        {
          id: 6,
          parentColumn: "Ready For Review",
          title: "MW-6",
          completed: false
        },
        {
          id: 7,
          parentColumn: "Ready For Review",
          title: "MW-7",
          completed: false
        }
      ],
      columnCounters: 
      {
        inProgressCounter: 0,
        readyForDeployCounter: 0,
        readyForReviewCounter: 0
      }
    }
  },
  created(){
    // axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    //   .then(Response => this.todoList = Response.data)
    //   .catch(err => console.log(err));
  },
  methods: {
    deleteItems(taskToDelete){
      if(taskToDelete.completed){
        if(taskToDelete.parentColumn === 'In Progress'){
          this.columnCounters.inProgressCounter--;
        }
        else if(taskToDelete.parentColumn === 'Ready For Deploy'){
          this.columnCounters.readyForDeployCounter--;
        }
        else if(taskToDelete.parentColumn === 'Ready For Review'){
          this.columnCounters.readyForReviewCounter--;
        }

        this.todoList = this.todoList.filter(item => item.id !== taskToDelete.id);
      }
      
    },
    approveItemAdd(newTodoItem){
      // const {title, completed } = newTodoItem
      this.todoList = [...this.todoList, newTodoItem];
      if(newTodoItem.parentColumn === 'In Progress'){
        this.columnCounters.inProgressCounter++;
      }
      else if(newTodoItem.parentColumn === 'Ready For Deploy'){
        this.columnCounters.readyForDeployCounter++;
      }
      else if(newTodoItem.parentColumn === 'Ready For Review'){
        this.columnCounters.readyForReviewCounter++;
      }
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
