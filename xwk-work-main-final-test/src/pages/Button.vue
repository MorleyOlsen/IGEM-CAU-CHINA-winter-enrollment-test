<template>
  <div class="flex gap-2 flex-col">
    <Nav></Nav>
    <div class="text-2xl font-bold m-8">
      欢迎来到第一个房间
    </div>
    <div>
      点击下面的按钮，即可获得随机数！
    </div>
    <div v-if="displayed" class="font-bold text-lg">
      恭喜你抽到{{ num }}
    </div>
    <button @click="() => {
      displayed = true;
      num = Math.floor(Math.random() * 10);
    }">
      Go!
    </button>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Nav from '../components/Nav.vue';

const num = ref(0)
const displayed = ref(false)

</script>