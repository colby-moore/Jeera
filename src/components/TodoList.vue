<template>
    <div>
        <b-container fluid class="bv-example-row">
            <b-row>
                <b-col class="column" sm="12" lg="4">
                    <p>IN PROGRESS: {{columnCounters.inProgressCounter}} </p>
                    <div v-bind:key="items.id" v-for="items in todoList">
                        <TodoListItem v-bind:items="items" v-if="items.parentColumn === 'In Progress'" v-on:del-items="$emit('del-items', items)"/>
                    </div>
                </b-col>
                <b-col class="column" sm="12" lg="4">
                    <p>READY FOR DEPLOY: {{columnCounters.readyForDeployCounter}} </p>
                    <div v-bind:key="items.id" v-for="items in todoList">
                        <TodoListItem v-bind:items="items" v-if="items.parentColumn === 'Ready For Deploy'" v-on:del-items="$emit('del-items', items)"/>
                    </div>
                </b-col>
                <b-col class="column" sm="12" lg="4">
                    <p>READY FOR REVIEW: {{columnCounters.readyForReviewCounter}} </p>
                    <div v-bind:key="items.id" v-for="items in todoList">
                        <TodoListItem v-bind:items="items" v-if="items.parentColumn === 'Ready For Review'" v-on:del-items="$emit('del-items', items)"/>
                    </div>
                </b-col>
            </b-row>
        </b-container>
    </div>
</template>

<script>
import TodoListItem from './TodoListItem.vue';

export default {
    name: "TodoList",
    props: ["columnCounters", "todoList"],
    data () {
        return{
           
        }
    },
    components: {
        TodoListItem
    },
    methods: {

    },
    created(){
        this.todoList.forEach(element => {
            if(element.parentColumn === 'In Progress'){
                this.columnCounters.inProgressCounter++;
            }
            else if(element.parentColumn === 'Ready For Deploy'){
                this.columnCounters.readyForDeployCounter++;
            }
            else if(element.parentColumn === 'Ready For Review'){
                this.columnCounters.readyForReviewCounter++;
            }
        });
    }
}
</script>

<style scoped>
    p{
        color: #5E6C84;
        font-size: 0.85714286em;
        font-weight: 600;
        line-height: 1.33333333;
        margin-top: 20px;
        text-transform: uppercase;
        display: inline-block;
        font-weight: normal;
        margin-top: 3px;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
    }
    .column{
        border-radius: 4px;
        background: #f4f4f4;
        border:5px solid white;
        padding: 5px;
        padding-bottom: 10px;
    }
    .column:first-child{
        border-left: 10px solid white;
    }
    .column:last-child{
        border-right: 10px solid white;
    }
</style>

