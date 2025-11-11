<!-- D1_App.vue -->


<template>
  <div class="container mt-4">
    <h1 class="display-4 mb-3">Thông tin khóa học</h1>

    <ul class="list-group">
      <li class="list-group-item">Tên khóa học: {{ courseName }}</li>
      <li class="list-group-item">Cấp độ: {{ courseLevel }}</li>
      <li class="list-group-item">Thời gian: {{ courseTime }} giờ</li>
      <li class="list-group-item">
        Trạng thái:
        <span :class="courseIsActive ? 'text-success' : 'text-danger'">
          {{ courseIsActive ? 'Đang mở' : 'Đã đóng' }}
        </span>
      </li>
    </ul>
  </div>
</template>

<script setup>
/*
  Khai báo biến trong Vue 3 Composition API
  Biến thông thường vẫn hiển thị được trong template
*/

let courseName = "Framework Vue 3"
let courseLevel = "Nâng cao"
let courseTime = 30
let courseIsActive = true
</script>

<style scoped>
.container {
  max-width: 600px;
}
</style>
