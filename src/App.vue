<template>
  <!-- 메뉴 -->
  <div class="menu">
    <a v-for="(a, i) in 메뉴들" :key="i">{{ a }}</a>
  </div>
  <!-- //메뉴 -->

  <!-- 모달창 -->
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <img :src="원룸들[누른거].image" alt="" class="modal-img" />
      <h4>{{ 원룸들[누른거].title }}</h4>
      <p>{{ 원룸들[누른거].price }}</p>
      <p>{{ 원룸들[누른거].content }}</p>
      <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div>
  <!-- //모달창 -->

  <!-- 리스트 -->
  <div v-for="(object, i) in 원룸들" :key="i">
    <img :src="원룸들[i].image" alt="" class="room-img" />
    <h4
      @click="
        모달창열렸니 = true;
        누른거 = i;
      "
    >
      {{ 원룸들[i].title }}
    </h4>
    <p>{{ 원룸들[i].price }} 만원</p>
  </div>
  <!-- //리스트 -->
</template>

<script>
import oneroom from './assets/oneroom';

export default {
  name: 'App',
  data() {
    return {
      누른거: 0,
      원룸들: oneroom,
      모달창열렸니: false,
      메뉴들: ['Home', 'Products', 'About'],
      price1: 60,
      price2: 70,
      products: ['역삼동 원룸', '천호동 원룸', '마포구 원룸'],
      신고수: [0, 0, 0],
    };
  },

  methods: {},

  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #001;
  text-align: center;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: #fff;
  padding: 10px;
  text-decoration: none;
  cursor: pointer;
}
.room-img {
  width: 100%;
  margin-top: 50px;
}

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
  left: 0;
  top: 0;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
h4 {
  cursor: pointer;
}
.modal-img {
  width: 100%;
}
</style>
