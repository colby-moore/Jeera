<template>
    <header class="header">
        <h1>Jeera2.0</h1>
        <div id="nav">
            <router-link to="/">Home</router-link> |
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
    .header{
        display: flex;
        align-items: center;
        justify-content: space-between;
        height: 70px;
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

