<template>
  <!--
    동적 UI (모달창) 
    1. 디자인부터 미리 만들기
    2. UI의 현재사애를 데이터로 만들기
    3. 
    -->
  <div class="black-bg" v-if="modal == true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지내용</p>
      <button @click="modal = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
  </div>
  
  <div v-for="(item, i) in room_data" :key="i">
    <img :src="room_data[i].image" class="room-img" />
    <h4>{{ room_data[i].content }}</h4>
    <p>{{ room_data[i].price }}</p>
  </div>
</template>

<script>
import data from "./data";

export default {
  name: "App",
  //데이터 바인딩
  //실시간 렌더링 할때 쓴다
  //UI
  data() {
    return {
      room_data: data,
      modal: false,
      menus: ["home", "Shop", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
      prices: [12, 36, 72],
      singo: [0, 0, 0],
    };
  },

  methods: {},
  components: {},
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
.white-bg button {
  align-content: left;
  margin-right: 20px;
  margin-left: 10px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-emg {
  width: 100%;
  margin-top: 40px;
}
</style>
