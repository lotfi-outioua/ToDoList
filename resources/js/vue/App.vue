<template>
    <div class="container">
        <div class="heading">
            <h2 id="title">Todo List</h2>
            <item-form
                v-on:reloadlist="getList()"
            />
        </div>
        <list-view
            :items="items"
            v-on:reloadlist="getList()"
        />
    </div>
</template>

<script>
import ItemForm from './ItemForm.vue';
import ListView from './ListView.vue'

export default {
    components: {
        ItemForm,
        ListView
    },
    data() {
        return {
            items: []
        }
    },
    methods: {
        getList() {
            axios.get('api/items')
            .then(response => {
                this.items = response.data;
            })
            .catch(error => {
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

.container {
    width: 500px;
    margin: auto;

}

.heading {
    background: #e6e6e6;
    padding: 10px;
}

#title {
    text-align: center;
}

</style>
