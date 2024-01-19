<template>
  <!-- 메뉴 -->
  <div class="menu">
    <a v-for="(a, i) in 메뉴들" :key="i">{{ a }}</a>
  </div>
  <!-- //메뉴 -->

  <transition name="fade">
    <ModalApple :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니" @closePopup="모달창열렸니 = false" />
  </transition>
  <!-- 할인 배너 -->
  <DiscountBanner v-if="showDiscount == true" :discountPercent="discountPercent" />
  <!-- //할인 배너 -->

  <!-- 정렬버튼 -->
  <button @click="priceSort()">가격 저렴한 순 정렬</button>
  <button @click="priceSortReverse()">가격 비싼 순 정렬</button>
  <button @click="abcSort()">가나다 순 정렬</button>
  <button @click="sortBack()">초기화</button>
  <!-- //정렬버튼 -->

  <!-- 리스트 -->
  <OneroomList
    v-for="(list, i) in 원룸들"
    :key="i"
    :원룸들="원룸들[i]"
    @openModal="
      모달창열렸니 = true;
      누른거 = $event;
    "
  />

  <!-- //리스트 -->
</template>

<script>
import oneroom from './assets/oneroom';
import DiscountBanner from './components/DiscountBanner.vue';
import ModalApple from './components/ModalApple.vue';
import OneroomList from './components/OneroomList.vue';

export default {
  name: 'App',
  data() {
    return {
      showDiscount: true,
      원룸들오리지널: [...oneroom],
      누른거: 0,
      원룸들: oneroom,
      모달창열렸니: false,
      메뉴들: ['Home', 'Products', 'About'],
      price1: 60,
      price2: 70,
      products: ['역삼동 원룸', '천호동 원룸', '마포구 원룸'],
      신고수: [0, 0, 0],
      discountPercent: 10,
    };
  },

  methods: {
    sortBack() {
      this.원룸들 = [...this.원룸들오리지널];
    },
    priceSort() {
      this.원룸들.sort(function (a, b) {
        return a.price - b.price;
      });
    },
    priceSortReverse() {
      this.원룸들.sort(function (a, b) {
        return b.price - a.price;
      });
    },
    abcSort() {
      this.원룸들.sort(function (a, b) {
        return a.title.localeCompare(b.title);
      });
    },
  },

  components: {
    DiscountBanner: DiscountBanner,
    ModalApple: ModalApple,
    OneroomList: OneroomList,
  },

  /* 숙제 */
  //1초마다 할인배너 1% 씩 감소 setInterval 활용
  //재랜더링 == 업데이트, 업데이트 되기 전에 훅을 걸어 모달창에 2를 입력시 3개월부터 한다는 알럿 팝업창띄우기
  mounted() {
    setInterval(() => {
      if (this.discountPercent > 0) {
        this.discountPercent--;
      } else if (this.discountPercent <= 0) {
        this.discountPercent;
        this.showDiscount = false;
      }
    }, 500);
  },
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
  max-width: 600px;
  margin: 0 auto;
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
.discount {
  background: #ddd;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}

.fade-enter-from {
  transform: translateY(-1100px);
}
.fade-enter-active {
  transition: all 0.3s;
}
.fade-enter-to {
  transform: translateY(0);
}
.fade-leave-from {
  transform: translateY(0);
}
.fade-leave-active {
  transition: all 0.3s;
}
.fade-leave-to {
  transform: translateY(-1100px);
}
</style>
