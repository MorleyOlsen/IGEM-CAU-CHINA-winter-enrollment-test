<template>
  <div>
    <Nav />
    <div class="text-2xl font-bold m-8">
      欢迎来到第四个房间
    </div>
    <div>
      点开一个笑话~
    </div>
    <div>
      PS：再点一次会隐藏当前笑话！
    </div>
    <button @click="show = !show;change(show)">
      Check It Out!
    </button>
    <Transition>
      <h1 v-if="show" style="align-self: auto;">
        {{ jokes[cnt].message }}
      </h1>
    </Transition>
  </div>
</template>

<script setup>
import Nav from '../components/Nav.vue';
import { ref } from 'vue';

const show = ref(false)
var cnt=0

function change(show){
  if(show == true) cnt++;
  if(cnt == 6) cnt=0;
}

const jokes = ref([
  {message: '强扭的瓜不甜，但很解渴。'},
  {message: '我不是草船,你的贱不要往我这里放。'},
  {message: '百度搜不到你，我去搜狗。'},
  {message: '钱不是万能的，有时候还需要支付宝。'},
  {message: '这不是胖，是对生活过敏导致的肿胀。'},
  {message: '耶稣的儿子是——椰子。'}
])

</script>