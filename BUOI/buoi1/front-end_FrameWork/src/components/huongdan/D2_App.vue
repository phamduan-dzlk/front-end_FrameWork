<!-- codelogic js -->
<script setup>
// c1 option API 
// c2:composition API: dung 2 tu khoa ref, reactive
    import{ref, reactive} from 'vue'
    // 1. dung ref voi kieu du lieu nguyen thuy
    let studentName = ref('pham Đức Duẩn');
    let studentEmail = ref("phamduanpin111@gmail.com");
    let studentAge = ref(18);
    let studentStatus = ref(true);
    
    let count = ref(0);
    //dùng reactive với kiểu dữ liệu đối tượng
    let state = reactive({amount:0, name:'abc',status:true})
    //c1 vieets hamf
    function increamentCount(){
        count.value ++;
    }
    
    const increamentAmount = ()=>{
        //tang gia tri amount

        state.amount ++;
    }
    let hovaten = ref('phamducduan');


    const registerRuntimeCompiler =()=>{
        alert('dăng ky thanh cong')
    }
    const hi = ()=>{
        alert('hihih')
    }
    let StyleString = 'font-size:20px; color:red';
    let logoUrl = ref("/public/img/image.png");
    let slogan = ref('chạy khỏi thế giới này');
</script>
<template>
  <h1>THông tin:</h1>
  <ul class="list-group">
    <li class="list-group-item">định danh:{{count}}</li>
    <li class="list-group-item">tên sinh viên:{{studentName}}</li>
    <li class="list-group-item">Email:{{studentEmail}}</li>
    <li class="list-group-item">tuổi sinh viên:{{studentAge}}</li>
    <li class="list-group-item">Trạng thái:{{studentStatus? 'đang học' :'đang bảo lưu'}}</li>
  </ul>
  COUNT:{{ count }}
  <button class="btn btn-primary" @click="increamentCount">Increament count</button>
  <!-- hien thi gia tri thuoc tinh cua doi tuong: -->
  AMOUNT:{{ state.amount }}
  <button class="btn btn-success" @click="increamentAmount">Increament amount</button>
  
  <div class="">

      <!-- <label for="">xin chao{{ hovaten }}</label> -->
      <input type="text" class="form-conytol" v-model="hovaten">
        <p>xin chao {{hovaten}}</p>
    </div>
    <hr>
    <h3>Event Binding</h3>
    <p>sư dụng sự kiện người dùng tương tác với html</p>
    <div class="">
        <h6>Bắt sự kiện click</h6>
        <button class="btn btn-primary" @click="registerRuntimeCompiler()">Dăng ký</button>
        <h6>su kien tương ta voi input</h6>
        <input type="text" name="" id="" @blur="hi()">
    </div>

    <hr>
    <p> class binding</p>
    <h3>v-binding: class dùng để binding ràng buộc các lớp css cho 1 phần tử</h3>
    <div v-binding:class="'active'">
        {{ hovaten }}
    </div>
    <p>class binding-doi tuong</p>
    <div :class="{active: state.amount>=3}" >
        {{ state.amount }}
    </div>
    <hr>
    <h3>STYLE BINDING</h3>
    <p>style chuỗi, đối tượng, điều kiện</p>
    <div :style="StyleString">this is a style div</div>
    <h3>kết hợp class binding và style binding</h3>
    <div :class="['card', state.status ?'active' : 'deactive']" :style="{backgroundColor:state.status ? 'lightgreen':'lightcoral'}">
        {{ state.name }} - {{ state.status }}
    </div>
    <hr>
    <h3>PROPERTI BINDING</h3>
    <p>sử dụng để fill giá trị vào các property của thẻ html</p>
    <p>ảnh</p>
    <img :src="logoUrl" alt="">
    <p>ca</p>
    <input type="text" class="control" v-bind:value="slogan" id="">
</template>
<!-- code css -->
<style scoped>
.active{
    background-color: green;
    color: white;
    padding:10px
}
.deactive{
    background-color: red;
    color: aliceblue;
    padding: 10px;
}
</style>