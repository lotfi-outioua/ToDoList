<template>
    <div>
        <div v-for="(item, index) in items" :key="index">
            <list-item
                :item="item"
                class="itemview"
                v-on:itemchanged="$emit('reloadlist')"
            />
        </div>
    </div>
</template>

<script>
import ListItem from './ListItem.vue'

export default {
    props: ['items'],
    components: {
        ListItem
    }
}
</script>

<style scoped>
.itemview {
    background: #e6e6e6;
    padding: 5px;
    margin-top: 5px;
}
</style>
