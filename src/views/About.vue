<template>
  <div class="about">
    <b-container class="container">
      <b-row>
        <h1>System dashboard</h1>
      </b-row>
    </b-container>
    <b-container class="container">
      <b-row>
        <b-col class="box intro" sm="12" lg="5">
           <h3>Introduction</h3>
           <h1>Welcome to Jeera</h1>
           <b-row class="text-row">
              <b-col class="imageBox"><img src="../assets/logo.png"></b-col>
              <b-col>
                <p>Not sure where to start? Check out the Jira 101 guide and Atlassian training course. <br> You can customize this text in the Administration section.</p>
              </b-col>
             
           </b-row>
        </b-col>
        <b-col class="box assigned" sm="12" lg="5" offset-lg="1" offset-sm="0">
           <h3>Assigned to Me</h3>
            <div v-bind:key="items.id" v-for="items in todoList" class="assignedTasks">
                <p>{{items.title}}</p>
            </div>

        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  props: ["columnCounters"],
  data (){
    return {
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
    }
  },
  // created(){
  //   axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
  //     .then(Response => this.todoList = Response.data)
  //     .catch(err => console.log(err));
  // },
}
</script>

<style scoped>
.text-row{
  overflow: hidden;
}
  .assignedTasks{
    border-radius: 4px;
    box-shadow: 0px 1px 2px 0px rgba(9, 30, 66, 0.25);
    background: #fff !important;
    margin-top: 10px;
    padding: 15px;
    border-bottom: 1px #ccc dotted !important;
  }
  .assignedTasks p{
    margin-bottom: 0px;
  }
  .container{
    margin-top: 50px;
  }
  .intro{
    overflow: scroll;
    max-height: 285px;
  }
  .box{
    border-top-width: 4px;
    border-top-style: solid;
    border-top-left-radius: 3px;
    border-top-right-radius: 3px;
    border-top-color: #2684ff;
    padding: 15px;
    border-radius: 4px;
    min-height: 285px;
    -webkit-box-shadow: 0px 2px 10px -5px rgba(0,0,0,0.75);
    -moz-box-shadow: 0px 2px 10px -5px rgba(0,0,0,0.75);
    box-shadow: 0px 2px 10px -5px rgba(0,0,0,0.75);
  }
  @media screen and (max-width: 991px) {
  .assigned{
    margin-top: 50px;
  }
}
.imageBox{
  text-align: center;
}
img{
  max-width: 125px;
}
</style>
