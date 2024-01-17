<template>
  <div class="menu">
    <a v-for="(a, i) in 메뉴들" :key="i">{{ a }}</a>
  </div>

  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
      <button>닫기</button>
    </div>
  </div>

  <div @click="모달창열렸니 = true">
    <img src="./assets/room0.jpg" alt="" class="room-img" />
    <h4>{{ 원룸들[0].title }}</h4>
    <p>{{ price1 }} 만원</p>
    <button @:click="신고수[0]++">허위매물신고</button>
    <span>신고수 : {{ 신고수[0] }}</span>
  </div>
  <div>
    <img src="./assets/room1.jpg" alt="" class="room-img" />
    <h4>{{ 원룸들[1].title }}</h4>
    <p>{{ price2 }} 만원</p>
    <button @:click="신고수[1]++">허위매물신고</button>
    <span>신고수 : {{ 신고수[1] }}</span>
  </div>
  <div>
    <img src="./assets/room2.jpg" alt="" class="room-img" />
    <h4>{{ 원룸들[2].title }}</h4>
    <p>XX 만원</p>
    <button @:click="신고수[2]++">허위매물신고</button>
    <span>신고수 : {{ 신고수[2] }}</span>
  </div>
</template>

<script>
import oneroom from './assets/oneroom';

export default {
  name: 'App',
  data() {
    return {
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
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
