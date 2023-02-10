<template>
  <div>
    <div class="text-2xl font-bold m-8">
      欢迎来到随机数生成屋
    </div>
    <div class="grid grid-cols-2 grid-rows-2 gap-2 text-lg">
      <router-link :to="room.page" v-for="(room, i) in rooms" :key="i" class="btn md:w-64">
        {{ room.name }}{{ room.icon }}
        <div class="text-sm font-light">
          {{ room.description }}
        </div>
      </router-link>
    </div>
  </div>
</template>

<script setup>

const rooms = [
  { page: 'Button', name: '按钮随机', description: '点击一个button元素后提供一个0-9的随机整数并展示在屏幕上',icon:'🖱️' },
  { page: 'Value', name: '数值随机',description:'设置一个数值n，可以生成n个随机数并分别展示在屏幕上',icon:'🔢' },
  { page: 'Time', name: '时间随机',description:'设置一个时间间隔t，每过t时间则自动生成随机数并展示在屏幕上',icon:'⏰' },
  { page: 'Happy', name: '开心麻花',description:'魔法屋的盲盒',icon:'😍' },
]
</script>
