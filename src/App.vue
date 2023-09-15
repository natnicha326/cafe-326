<script setup>
  import{ ref } from "vue";

  const travel = ref("");
  const Details = ref({
    name: "",
    tel: "",
    date: "",
    time: "",
    tables: ""
  });
  
  const travelList = ref([
    {name:'Treespresso cafe ', price:80, size: {s:80, m: 150, l: 200}, img:"https://www.ryoiireview.com/upload/article/202304/1681731156_d018557a4a10aed6c8f450ad0db6d60d.jpg" },
    {name:'Simply Happy cafe', price: 50 , size: {s:50, m: 100, l: 150}, img:"https://www.ryoiireview.com/upload/article/202111/1636963137_cf5793938b321b67b3b667655b375703.jpg" },
    {name:'Polaris Sunrise Café', price: 90 , size: {s:90, m: 120, l: 150}, img:"https://www.ryoiireview.com/upload/article/202304/1681733919_1dc9da5619cecf386917f0533fd4ce31.jpg" },
    {name:'Chapter 2WO', price: 100 , size: {s:100, m: 150, l: 200}, img:"https://www.ryoiireview.com/upload/article/202304/1681732353_3374a1e478e443690a89fcfb04c52150.jpg" },
    {name:'MYTH OVEN', price: 30 , size: {s:30, m: 50, l: 100}, img:"https://www.ryoiireview.com/upload/article/202304/1681733535_ceea4fe6aece45f4d4e266a93599e4d0.jpg" }, 
    {name:'Nuan cafe & bistro', img:"https://www.ryoiireview.com/upload/article/202304/1681707959_4a870111f80d82cea86ea6a0a43a04e5.jpg"}
  ]);
  
  const cafeList = ref([
  ]);

  

  function cafe(cafe, details) {

  const cafeData = {
    cafeName: cafe.name,
    name: details.name,
    tel: details.tel,
    date: details.date,
    time: details.time,
    tables: details.tables,
  };

  cafeList.value.push(cafeData);

  Details.value.name = '';
  Details.value.tel = '';
  Details.value.date = '';
  Details.value.time = '';
  Details.value.tables = '';
  /*alert("ขอบคุณสำหรับการทำรายการ");*/
      /*const name = prompt("ชื่อ:");
      const phone = prompt("เบอร์โทร:");
      const date = prompt("วันที่:");
      const time = prompt("เวลา:");
      const tables = prompt("จำนวนโต๊ะ");*/
      if (name && phone && date && time && tables) {
        this.cafe = {
          name,
          phone,
          date,
          time,
          tables,
        };
      }
      
}


  

</script>

<template>
  
  <h1 style="color: rgb(255, 250, 250) ;">🍦Select your like cafe☕</h1> <br>
  <div class="container-input" style="background-color: #e14d8a;">
    <h4 style="color: rgb(255, 251, 251); font-weight: bold;">กรุณากรอกข้อมูลให้ครบถ้วน </h4>
    <div class="cont">
          <div class="text-input">
            Name &nbsp; <input type="text" v-model="Details.name" required> 
          </div>
          <div class="text-input">
            phone &nbsp; <input type="tel" v-model="Details.tel" required> 
          </div>
          <div class="text-input">  
            DD/MM/YYYY &nbsp; <input type="date" v-model="Details.date" required>
          </div>
          <div class="text-input">
            Time &nbsp; <input type="time" v-model="Details.time" required>
          </div>
          <div class="text-input">
            Tables &nbsp; <input type="number" v-model="Details.tables" required> 
          </div>
    </div>

  </div>
  <div class="container text-center" style="background-color: ; border-radius: 20px;">
    <div class="row" align="center">
      <div class="col" v-for="(item, index) in travelList" :key="index">
        <div class="card" style="width: 18rem; background-color: #ec89b4; margin: 25px; border-radius: 30px;">
          <img :src="item.img" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">{{ item.name }}</h5>
            <p class="card-text">เปิดให้บริการ:08.00-20.00 น</p>
             <br>
             <p class="card-text">ยินดีต้อนรับ</p>
             <br>
            <a href="#" class="btn" @click="cafe(item, Details)">จองโต๊ะ</a>
          </div>
        </div>
      </div>
    </div>
  </div> <br>
  <div v-if="cafe">
      <h2>รายละเอียดการจอง</h2>
      <p>ชื่อ: {{ Details.name}}</p>
      <p>เบอร์โทร: {{ Details.tel }}</p>
      <p>วันที่: {{ Details.date }}</p>
      <p>เวลา: {{ Details.time }}</p>
      <p>จำนวนโต๊ะ: {{ Details.tables }}</p>
    </div>
</template>
