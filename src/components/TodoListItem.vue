<template>
    <div class="todo-list-item" v-bind:class="{'is-completed':items.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete">
            {{items.title}}
            <button @click="$emit('del-items', items.id)" class="del">X</button>
        </p>
    </div>
</template>

<script>
export default {
    name: "TodoListItem",
    props: ["items"],
    methods: {
        markComplete(){
            this.items.completed = !this.items.completed;
        }
    }
}
</script>

<style scoped>
    p{
        margin-bottom: 0;
    }
    .todo-list-item{
        background: #f4f4f4;
        padding: 30px;
        border-bottom: 1px #ccc dotted;
    }

    .is-completed{
        text-decoration: line-through;
    }

    .del{
        background: #555;
        color: #fff;
        border: none;
        border-radius: 50%;
        cursor: pointer;
        float: right;
        height: 22px;
        width: 22px;
    }
</style>

