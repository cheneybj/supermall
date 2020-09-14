<template>
  <swiper v-if="banners.length > 0">
    <swiper-item v-for="item in banners">
      <a :href="item.link">
        <img :src="item.image" alt="">
      </a>
    </swiper-item>
  </swiper>
</template>

<script>
import { Swiper, SwiperItem } from "components/common/swiper";

export default {
  props: {
    banners: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  components: {
    Swiper,
    SwiperItem,
  },
  methods: {
    startTimer() {
      this.$refs.swiper && this.$refs.swiper.startTimer();
    },
    stopTimer() {
      this.$refs.swiper && this.$refs.swiper.stopTimer();
    },
    imageLoaded() {
      if (!this.isLoaded) {
        this.$emit("swiperLoaded");
        this.isLoaded = true;
      }
    },
  },
};
</script>

<style>
</style>
