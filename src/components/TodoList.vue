<template>
    <div>
       <div v-bind:key="items.id" v-for="items in todoList">
           <TodoListItem v-bind:items="items" v-on:del-items="$emit('del-items', items.id)"/>
       </div>
    </div>
</template>

<script>
import TodoListItem from './TodoListItem.vue';

export default {
    name: "TodoList",
    components: {
        TodoListItem
    },
    props: ["todoList"]
}
</script>

<style scoped>

</style>

