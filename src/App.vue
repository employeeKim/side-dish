<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const message = ref('')

onMounted(() => {
  axios.get('http://localhost:8081/common/test')
    .then(res => {
      message.value = res.data.message
    })
    .catch(err => {
      console.error('API 호출 실패:', err)
      message.value = 'API 호출 에러'
    })
})
</script>

<template>
  <div>
    <a href="https://vite.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>

    <!-- 여기가 추가 부분입니다 -->
    <p>서버 응답: {{ message }}</p>

    <HelloWorld msg="Vite + Vue" />
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
