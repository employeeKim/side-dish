<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
</script>

<template>
  <div>
    <h1>반찬가게 테스트</h1>
    <p>응답: {{ message }}</p>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  data() {
    return {
      message: ''
    }
  },
  mounted() {
    axios.get('http://localhost:8081/api/test')
      .then(res => {
        this.message = res.data.message
      })
      .catch(err => {
        console.error('API 호출 실패: ', err)
        this.message = 'API 호출 에러'
      })
  }
}
</script>


<style scoped>
.read-the-docs {
  color: #888;
}
</style>
