<template>
  <div class="flex gap-2">
    <RouterLink class="btn" to="/">首页</RouterLink>
    <RouterLink v-for="room in rooms" class="btn" :to="room.url" :class="room.url === route.path ? 'text-red-300' : ''">
      {{ room.name }}
    </RouterLink>
  </div>
</template>

<script setup>
import { useRoute } from 'vue-router'
const route = useRoute()
const rooms = [
  { url: '/Button', name: '按钮随机' },
  { url: '/Value', name: '数值随机' },
  { url: '/Time', name: '时间随机' },
  { url: '/Happy', name: '开心麻花' },
]
</script>