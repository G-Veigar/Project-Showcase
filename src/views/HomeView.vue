<script setup lang="ts">
import { useRouter } from 'vue-router'
import { showcaseList } from '../showcase'

const router = useRouter()

function goDetail(title: string) {
  router.push({
    name: 'detail',
    params: {
      title
    }
  })
}
</script>

<template>
  <div class="home-page">
    <div class="showcase-wrapper">
      <div 
        class="showcase-item"
        v-for="item in showcaseList"
        :key="item.title"
        @click="goDetail(item.title)">
        <div class="img-wrapper">
          <img class="showcase-img" :src="item.img" alt="showcase">
        </div>
        <div class="showcase-desc">{{item.title}}</div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.home-page {
  display: flex;
  justify-content: center;
  min-height: 100vh;
  box-sizing: border-box;
  background: url('../assets/wave.svg') no-repeat;
  background-position: 0% 100%;
  background-size: 100%;
  padding-top: 30px;
  padding-bottom: 100px;
}

.showcase-wrapper {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
}

.showcase-item {
  font-size: 14px;
  display: flex;
  flex-direction: column;
  align-items: center;
  /* width: 40%; */
  /* max-width: 100px; */
  margin-bottom: 20px;
  cursor: pointer;
}

.showcase-desc {
  margin-top: 6px;
}

.img-wrapper {
  width: 40vw;
  height: 40vw;
  background-color: #ddd;
  transition: transform 0.2s;
}

.showcase-img {
  object-fit: contain;
  width: 100%;
  height: 100%;
}

/* .showcase-item:hover .showcase-desc {
  color: #2b09ed;
}

.showcase-item:hover .img-wrapper {
  transform: scale(1.1);
} */
</style>
