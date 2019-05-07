<template>
    <div class="todo-list-item" v-bind:class="{'is-completed':items.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete">
            {{items.title}}
            <button @click="$emit('del-items', items)" class="del">X</button>
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
        border-radius: 4px;
        box-shadow: 0px 1px 2px 0px rgba(9, 30, 66, 0.25);
        background: #fff;
        margin-top: 10px;
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

