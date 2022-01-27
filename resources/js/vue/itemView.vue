<template>
    <div class="">
        <div v-for="(item, index) in items" :key="index">
            <item-list
                :item="item"
                class="item"
                v-on:itemChanged = "$emit('reloadList')"
            />
        </div>
    </div>
</template>

<script>
import itemList from "./itemList"
export default {
    props: ['items'],
    components: {
        itemList
    }
}
</script>

<style scoped>
    .item{
        background: #f5f5f5;
        padding: 5px;
        margin-top: 5px;
    }
</style>