<template>
  <div>
    <Modal @modalClose="modalOpen=false;" :rooms="rooms" :pressed="pressed" :modalOpen="modalOpen"> </Modal>

    <div class="menu">
      <a v-for="(a, index) in menu" :key="index" href="">{{ a }}</a>
    </div>

    <Discount></Discount>

    <Card
      @modalOpen="modalOpen=true; pressed=$event"
      v-for="(room, index) in rooms"
      :key="index"
      :room="rooms[index]"
    ></Card>

    <!-- <div v-for="(product, index) in rooms" :key="index">
      <img :src="rooms[index].image" class="room-img" />
      <h3
        v-on:click="
          modalOpen = true;
          pressed = index;
        "
      >
        {{ rooms[index].title }}
      </h3>
      <p>{{ rooms[index].price }} 원</p>
    </div> -->
  </div>
</template>

<script>
import oneRoom from "./assets/oneroom.js";
import Discount from "./components/Discount.vue";
import Modal from "./components/Modal.vue";
import Card from "./components/Card.vue";

export default {
  name: "App",
  data() {
    return {
      pressed: 0,
      rooms: oneRoom,
      modalOpen: false, //모달창 false: 닫힌 상태, true: 열린 상태
      menu: ["Home", "Shop", "About"], //상단 메뉴바
      products: ["역삼동 원룸", "천호동 원룸", "마포구 원룸"], //제품 목록
      report: [0, 0, 0], //신고 수
    };
  },
  methods: {
    increase(i) {
      //신고 버튼 작동 시 신고 수++
      this.report[i]++; //this = 내 오브젝트
    },
  },
  components: {
    Discount: Discount,
    Modal: Modal,
    Card: Card,
  },
};
</script>

<style>
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
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

.room-img {
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}
</style>
