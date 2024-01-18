<template>
  <div>
    <img :src="원룸들.image" alt="" class="room-img" />
    <h4 @click="send()">
      {{ 원룸들.title }}
    </h4>
    <p>{{ 원룸들.price }} 원</p>
  </div>
</template>

<script>
export default {
  name: 'OneroomList',
  props: {
    원룸들: Array,
  },
  methods: {
    send() {
      this.$emit('openModal', this.원룸들.id);
    },
  },
};
</script>

<style></style>
