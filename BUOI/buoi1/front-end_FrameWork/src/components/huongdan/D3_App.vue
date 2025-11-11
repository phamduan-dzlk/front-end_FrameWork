<script setup>
    import {ref,reactive} from 'vue';
    let age = ref(19);
    let score = ref(80);
    //hàm chuyển đổi trạng thái hiển thị
    let isAbsen = ref(true);
    const toggleAlbsent = () =>{
        isAbsen.value = !isAbsen.value
    }

    // mảng đối tượng
    let list_foods = reactive([
        {
            id:'F01',
            name:'Bún bò huế',
            quantity:10,
            price:3000
        },
        {
            id:'F02',
            name:'Bún sốt cà chua',
            quantity:15,
            price:5000
        },
        {
            id:'F03',
            name:'cơm rang dưa bò',
            quantity:10,
            price:3000
        }
    ]);
    const totalCartValue = ()=>{
        return list_foods.reduce((total, item)=>{
            return total + item.price * item.quantity;
        },0)
    }
</script>
<template>
    <div class="container">
        <h3>V_IF / V-ELSE</h3>
        <div v-if=" age >18" class="alert alert-success mt-4">ban da du tuoi</div>
        <div v-else class="alert alert-danger mt-4">ban tuoi lol</div>
    </div>
    <div>
        <p>thông báo xếp hạng</p>
        <span v-if="score>=90">Xuất sắc</span>
        <span v-else-if="score>=80">giỏi</span>
        <span v-else-if="score>=70">khá</span>
        <span v-else-if="score>=50">trung bình</span>
        <span v-else>yếu vl</span>
    </div>
    <h3>v-show: check diem danh</h3>
    <div v-show="!isAbsen" class="alert alert-success">có mặt</div>
    <div v-show="isAbsen" class="alert alert-warning">vắng mặt</div>
    <button class="btn btn-primary" @click="toggleAlbsent" :class="isAbsen ? 'btn btn-danger' : 'btn btn-primary'">
        {{ isAbsen ? 'vắng mặt ':'có mặt' }}
    </button>
    <ul v-for="list in list_foods" :key="list.id">
        <li>{{ list }}</li>
    </ul>
    <p>dnah sách món ăn kèm theo index</p>
    <ul v-for="(item, index) in list_foods" :key="item">
        <li>{{ index }} - {{ item.price * item.quantity }}</li>
    </ul>
    <!-- hiển thị giỏ hàng -->
     <table class="table">
        <thead>
            <tr>
                <td>ID</td>
                <td>Tên</td>
                <td>Đơn giá</td>
                <td>Số lượng</td>
                <td>Số TIền</td>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(food, index) in list_foods" :key="food.id">
                <td>{{ food.id }}</td>
                <td>{{ food.name }}</td>
                <td>{{ food.price }}</td>
                <td>{{ food.quantity }}</td>
                <td>{{ food.price * food.quantity }}</td>
            </tr>
        </tbody>
     </table>
     <h2>Tổng tiền giỏ hàng: {{ totalCartValue() }}</h2>
</template>
<style scoped></style>