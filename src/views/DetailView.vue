<script setup lang="ts">
import { computed } from 'vue';
import { useRoute, useRouter } from 'vue-router'
import { showcaseList } from '@/showcase';

const { params } = useRoute()
const router = useRouter()

const projectInfo = computed(() => {
  return showcaseList.find(item => item.title === params.title)
})

const goBack = () => {
  router.back()
}
</script>

<template>
  <div class="project-detail">
    <div class="project-title">
      <button class="back-btn" @click="goBack"></button>
      {{ params.title }}
    </div>
    <van-swipe class="my-swipe" :autoplay="false" :loop="false" indicator-color="white">
      <van-swipe-item v-for="(item, index) in projectInfo?.cases" :key="index">
        <img class="project-object" v-if="item.type === 'img'" :src="item.src" alt="">
        <video class="project-object" v-if="item.type === 'vedio'" :src="item.src" controls preload="auto"></video>
      </van-swipe-item>
    </van-swipe>
  </div>
</template>

<style scoped>
.back-btn {
  background: url('../assets/back.svg') center center no-repeat;
  width: 30px;
  height: 30px;
  border: none;
  background-size: 70%;
  position: absolute;
  left: 12px;
  top: 50%;
  transform: translateY(-50%);
}
.project-detail {
  min-height: 100vh;
  background-color: black;
}
.project-title {
  position: relative;
  color: #fff;
  text-align: center;
  font-size: 20px;
  height: 36px;
  line-height: 36px;
  margin-bottom: 10vh;
}

.my-swipe .van-swipe-item {
  color: #fff;
  font-size: 20px;
  height: 70vh;
  text-align: center;
  background-color: black;
}

.project-object {
  object-fit: contain;
  width: 100%;
  height: 100%;
}
</style>
