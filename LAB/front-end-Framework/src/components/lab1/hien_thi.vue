<!-- noi code --> 
<script setup>
    import {ref,reactive} from 'vue'
    let name = ref('lan');
    let age = ref(18)
    let description = reactive([
            {
                id:1,
                name:'duan',
                age:18
            },
            {
                id:2,
                name:'huy',
                age:182
            }              
        ]
    )
    console.log(description);
    
    let stt = 0;
    let change_introduction = ()=>{
        name.value = description[stt].name;
        age.value = description[stt].age ;
        stt++;
    }
</script>
<template>
    <h1> xin chao tat ca moi nguoi nha em la {{ name }} tuoi:{{ age }}</h1>
    <button class="btn btn-primary" @click="change_introduction()"> số báo danh: <trong>{{stt}}</trong> nhấn để giới thiệu vầ bản thân nhanh</button>
</template>
<style scoped></style>