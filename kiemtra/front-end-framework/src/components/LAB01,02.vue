<script setup>
import {ref,reactive} from 'vue';
const products = reactive([{


    "id": 1,


    "img_cover":
"https://example.com/images/sach1.jpg",


    "title": "Sách 1",


    "author": "Tác giả 1",


    "category": "Danh mục1",


    "quantity": 10


  },


  {


    "id": 2,


    "img_cover":
"https://example.com/images/sach2.jpg",


    "title": "Sách 2",


    "author": "Tác giả 2",


    "category": "Danh mục2",


    "quantity": 123


  },


  {


    "id": 3,


    "img_cover":"https://example.com/images/sach3.jpg",


    "title": "Lập trình Python từ cơ bản đến nâng cao",


    "author": "Nguyễn Văn A",


    "category": "Công nghệ thông tin",


    "quantity": 45


  },


  {


    "id": 4,


    "img_cover":
"https://example.com/images/sach4.jpg",


    "title": "Tâm lý học thành công",


    "author": "Trần Thị B",


    "category": "Phát triển bản thân",


    "quantity": 0


  }]);
  let create = ref(true);
  const show = ()=>{
    create.value = !create.value;
  }

  let resultName = ref(true);
  let result = ref(true);
  let messageName = ref('');
  let message = ref('');
  const checkempty = ()=>{
    let name = document.querySelector("#name").value;
    let quantity = document.querySelector("#quantity").value;
    if(name == ''){
      messageName.value = 'Bạn không được để chống tên';
      resultName.value = false;
    }else{
      messageName.value = '';

    }
    if(quantity == ''){
      message.value = 'bạn không được để chống số lượng';
      result.value = false;
    }else{
      message.value = '';

    }
  }
  let isconfirm = ()=>{
    confirm('bạn có muốn xóa không!');
  }
</script>
<template>
 <h1>hhhihiih</h1>
        <button class="btn btn-success" @click="show">tao moi</button>

 <table class="table">
    <thead><tr>
        <th>id</th>
        <th>img</th>
        <th>title</th>
        <th>author</th>
        <th>category</th>
        <th>quantity</th>
    </tr></thead>
    <tbody>
        <tr v-for="items in products" :key="items.id">
        <th>{{items.id}}</th>
        <th><img :src=" items.img_cover " alt=""></th>
        <th>{{items.title}}</th>
        <th>{{items.author}}</th>
        <th>{{items.category}}</th>
        <th>{{items.quantity}}</th>
        <th>
            <p v-if=" items.quantity == 0   " style="color: red;">hết hàng</p>
            <p v-else="" style="color: green;">Còn hàng</p>
        </th>
        <td>
            <button class="btn btn-primary">xem</button>
            <button class="btn btn-success">sửa</button>
            <button class="btn btn-danger" @click="isconfirm">xóa</button>
        </td>
        </tr>
    </tbody>
 </table>
 <div class="container p-10" style="border:1px solid red; box-shadow: 0 2px 2px red;">
   <form @submit.prevent="checkempty" :class= " create ? 'hidden' : ' show'">
     <div class="mb-3">
       <label for="exampleInputEmail1" class="form-label">ten sach</label>
       <input type="text" class="form-control"  id="name" >
       <div id="textHelp" class="form-text" :class=" resultName ? 'hidden':'error' "> {{ messageName }} </div>
     </div>
     <div class="mb-3">
       <label for="exampleInputPassword1" class="form-label">So luong</label>
       <input type="number" class="form-control"  id="quantity">
       <div id="textHelp" class="form-text" :class=" result ? 'hidden':'error' "> {{ message }} </div>
 
     </div>
     <button type="submit" class="btn btn-primary" >Submit</button>
   </form>
 </div>
</template>
<style scoped>
.hidden{
  display: none;
}
.show{
  display: block;
}
.error{
  color:red;
  display: block;
}
</style>