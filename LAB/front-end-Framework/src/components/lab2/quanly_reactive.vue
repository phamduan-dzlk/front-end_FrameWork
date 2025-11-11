<script setup>

import {ref,reactive} from 'vue'
let user = reactive(
    {
        name:'',
        age:null,
        email:''
    }
)
let submitForm = ()=>{
    // if(user.name && user.email){
    //     alert('thông tin không hợp lệ!')
    // }else{
    //     alert('vui lòng nhập đầy đủ thông tin!');
    // }
}
let isActive = ref(false);
let fontSize = ref(16);
</script>
<template>
    <div class="container">

        <h1>Quan ly thong tin dung voi reactive()</h1>
        <form @submit.prevent="submitForm">
            <label for="">Ten: <input type="text" v-model="user.name" required></label>
            <label for="">Tuoi: <input type="number" v-model="user.age" required></label>
            <label for="">Email: <input type="text" v-model="user.email" required></label>
            <button class="btn btn-primary" type="submit">cap nhap</button>
        </form>
        <p>ten:{{ user.name }}</p>
        <p>ten:{{ user.age }}</p>
        <p>ten:{{ user.email }}</p>


        <h1 :class="{active:isActive}" :style="{fontSize:fontSize + 'px'}">van ban co the thay doi</h1>
        <button class="btn btn-primary" @click="isActive = !isActive">bat/tat mau chu</button>
        <label for="">chon kich thuc chu: <input type="number" v-model="fontSize" ></label>
        <p v-if="fontSize <10 || fontSize > 50">Kich thuoc khong hop le</p>
    </div>
</template>
<style scoped>
    .active{
        color:rgb(255, 0, 0);
    }
</style>