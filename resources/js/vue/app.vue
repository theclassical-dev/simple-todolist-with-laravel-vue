<template>
    <div class="todoListContainer">
       <div class="heading">
            <h2 id="title">Todo List</h2>
            <item-form  v-on:reloadList= "getList()" />
       </div>
       <item-view :items = "items" v-on:reloadList= "getList()" />
    </div>

</template>

<script>
import itemForm from "./itemForm"
import itemView from "./itemView"

export default {
    components: {
        itemForm,
        itemView
    },
    data() {
        return {
            items: []
        }
    },
    methods: {
        getList () {
            axios.get('api/items')
            .then( response => {
                this.items = response.data
            })
            .catch( error => {
                console.log(error);
            })
        }
    },
    created() {
        this.getList();
    }

}
</script>

<style scoped>
    .todoListContainer {
        width:500px;
        margin:auto;
        margin-top:150px;
    }

    .heading {
        background: #f5f5f5;
        padding: 10px;
    }

    #title {
        text-align: center;
    }
</style>