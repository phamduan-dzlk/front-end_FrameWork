<script setup>
    import {reactive} from 'vue'
    let product= reactive([
        {
            id:1,
            name:'may tinh',
            price:123123
        },
        {
            id:1,
            name:'may tinh',
            price:123
        }
    ]);

</script>
<template>
    <table class="table">
        <tr>
            <th>id</th>
            <th>ten</th>
            <th>gia</th>
        </tr>
        <tbody >
        <tr v-for="item in product" :key = "item.id">
            <th>{{item.id}}</th>
            <th>{{item.name}}</th>
            <th>{{item.price}}</th>
        </tr>

        </tbody>
    </table>
</template>
<style scoped>
</style>