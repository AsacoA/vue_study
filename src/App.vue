<template>
  <!--동적 UI (모달창)
1. 디자인부터 미리 만들기
2. UI의 현재사애를 데이터로 만들기
3.
  -->

  <div class="black-bg" v-if="modal_status == true" @click.self="closeModal">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지내용</p>
    </div>
  </div>

  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
  </div>

  <div v-for="(it, i) in room_data" :key="i">
    <img @click="openModal" class="room-img" :src="room_data[i].image" />
    <h4 @click="openModal">{{ room_data[i].content }}</h4>
    <p>보증금 : {{room_data[i].price}} 만원</p>
    <hr />
  </div>
</template>

<script>
import data from "./assets/data";

export default {
  name: "App",
  //데이터 바인딩
  //실시간 렌더링 할때 쓴다
  //UI
  data() {
    return {
      room_data: data,
      modal_status: false,
      menus: ["home", "Shop", "About"],
    };
  },
  methods: {
    closeModal() {
      this.modal_status = false;
    },
    openModal() {
      this.modal_status = true;
    },
    // eslint-disable-next-line no-unused-vars
  },
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
  margin-left: 80%;
  margin-top: 3%;
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
