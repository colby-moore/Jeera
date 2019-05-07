<template>
    <div>

        <b-modal id="modalAddItem" title="Add Item">
            <!-- <p class="my-4">{{title}}</p> -->
            <textarea class="modal-input" type="text" v-model="title" placeholder="Add a task for the day"></textarea>
            <select class="modal-select" v-model="parentColumn">
                <option disabled value="">Choose a column:</option>
                <option>In Progress</option>
                <option>Ready For Deploy</option>
                <option>Ready For Review</option>
            </select>

           <template slot="modal-footer" slot-scope="{ cancel, ok }">

               
                <b-button size="sm" class="submit" variant="success" @click="() => { ok(); submitTodoItem(); }">
                    <b>Create</b>
                </b-button>
                
                <b-button size="sm" class="cancel" variant="danger" @click="cancel()">
                    Cancel
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
            parentColumn: ''
        }
    },
    methods:{
        submitTodoItem() {
            const newTodoItem = {
                title: this.title,
                parentColumn: this.parentColumn,
                completed: false,
            }
            // emit to app vue which is the parent that holds this data
            this.$emit('parse-submit', newTodoItem);
            this.title = '';
            this.parentColumn = '';
        }
    }
}
</script>

<style scoped>
    .submit{
        border: none;
        background: #0747A6;
    }

    .cancel{
        border: none;
        color: #0052cc;
        background: transparent;
    }
</style>

