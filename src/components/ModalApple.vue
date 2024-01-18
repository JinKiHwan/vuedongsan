<template>
  <!-- 모달창 -->
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <img :src="원룸들[누른거].image" alt="" class="modal-img" />
      <h4>{{ 원룸들[누른거].title }}</h4>
      <p>{{ 원룸들[누른거].content }}</p>

      <input type="number" v-model.number="month" />

      <p>{{ month }}개월 선택함 : {{ 원룸들[누른거].price + month }} 원</p>
      <button @click="$emit('closePopup')">닫기</button>
    </div>
  </div>
  <!-- //모달창 -->
</template>

<script>
export default {
  name: 'ModalApple',
  props: {
    원룸들: Array,
    모달창열렸니: Boolean,
    누른거: Number,
  },
  data() {
    return {
      month: 1,
    };
  },
};
</script>

<style></style>
