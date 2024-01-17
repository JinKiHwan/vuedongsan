<template>
  <div class="menu">
    <a v-for="(a, i) in 메뉴들" :key="i">{{ a }}</a>
  </div>

  <div>
    <h4>{{ products[0] }}</h4>
    <p>{{ price1 }} 만원</p>
    <button @:click="increase">허위매물신고</button>
    <span>신고수 : {{ 신고수 }}</span>
  </div>
  <div>
    <h4>{{ products[1] }}</h4>
    <p>{{ price2 }} 만원</p>
    <button @:click="increase">허위매물신고</button>
    <span>신고수 : {{ 신고수 }}</span>
  </div>
  <div>
    <h4>{{ products[2] }}</h4>
    <p>XX 만원</p>
    <button @:click="increase">허위매물신고</button>
    <span>신고수 : {{ 신고수 }}</span>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      메뉴들: ['Home', 'Products', 'About'],
      price1: 60,
      price2: 70,
      products: ['역삼동 원룸', '천호동 원룸', '마포구 원룸'],
      신고수: 0,
    };
  },

  methods: {
    increase() {
      this.신고수++;
    },
  },

  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #000;
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
</style>
