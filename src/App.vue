<template>
  <div id="app">
    <Header />
    <router-view/>
  </div>
</template>

<script>
import Header from './components/layout/Header';
export default {
  name: "app",
  components: {
    Header
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
