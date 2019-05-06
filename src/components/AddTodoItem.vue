<template>
    <div>

        <b-modal id="modalAddItem" title="Add Item">

            <p class="my-4">{{title}}</p>
            <textarea class="modal-input" type="text" v-model="title" placeholder="Add a task for the day"></textarea>
            <!-- <button v-on:click="addMorningList">Morning Task</button>
            <button v-on:click="addAfternoonList">Afternoon Task</button>
            <button v-on:click="addNightList">Night Error in v-on handler: "TypeError: Cannot read property 'post' of undefined"Task</button> -->
            <select class="modal-select">
                <option disabled value="">Choose a column:</option>
                <option>Morning</option>
                <option>Afternoon</option>
                <option>Night</option>
            </select>

           <template slot="modal-footer" slot-scope="{ cancel, ok }">
                
                <b-button size="sm" variant="danger" @click="cancel()">
                    Cancel
                </b-button>

                <b-button size="sm" variant="success" @click="() => { ok(); submitTodoItem(); }">
                    Submit
                </b-button>
                <!-- Button with custom close trigger value -->
            </template>
        </b-modal>
    </div>
</template>

<script>

export default {
    name: "AddTodoItem",
    data(){
        return{
            title: '',
        }
    },
    methods:{
        submitTodoItem() {
            const newTodoItem = {
                title: this.title,
                completed: false,
            }
            // emit to app vue which is the parent that holds this data
            this.$emit('parse-submit', newTodoItem);
            this.title = '';
        }
    }
}
</script>

<style>

</style>

