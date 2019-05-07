<template>
    <header class="header">
        <h1><b>Jeera2.0</b></h1>
        <div id="nav">
            <router-link to="/">Kanban Board</router-link> |
            <router-link to="/about">About</router-link>
        </div>
        <b-button class="modal-button" v-b-modal.modalAddItem><b>+</b></b-button>
    </header>
</template>

<script>

export default {
    name: "Header"
}
</script>

<style scoped>
    h1{
        font-size: 1.5rem;
        margin-bottom: 0px;
    }
    .header{
        display: flex;
        align-items: center;
        justify-content: space-between;
        height: 60px;
        background: #0747A6;
        color: #fff;
        padding: 10px;
    }

    .header a{
        color: #fff;
        padding-right: 5px;
    }

    .modal-button{
        font-size: 24px;
        padding: 2.5px 10px;
    }
</style>

