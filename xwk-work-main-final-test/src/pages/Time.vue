<template>
  <div class="">
    <Nav />
    <div class="text-2xl font-bold m-8">
      欢迎来到第三个房间
    </div>
    <div>
      请在下面输入框中输入生成随机数的间隔时间t！
    </div>
    <div>
      默认的时间单位为秒（s）
    </div>
    <div>
      如果您需要转换：1s=1000ms; 1min=60s;
    </div>
    <div class="text-sm text-red-400">
      {{ countError }}
    </div>
    <div class="mt-8 flex gap-2 justify-center items-center">
      <input type="text" class="p-2 rounded-md bg-slate-100 dark:bg-zinc-700" v-model="count">s
      <button @click="handleGo" :disabled="!isValid && state === 'Go!'"
        class="disabled:opacity-50 disabled:cursor-not-allowed">
        {{ state }}
      </button>
    </div>

    <div v-if="typeof num === 'number'" class="font-bold text-lg mt-4">
      {{ num }}
    </div>
  </div>
</template>


<script setup>
import { ref } from 'vue';
import { useField, useForm, useIsFormValid } from 'vee-validate'
import * as yup from 'yup'
import Nav from '../components/Nav.vue';

const state = ref('Go!') //还有一个状态为Stop
const num = ref()

let intervalHandler = -1
const handleGo = () => {
  if (state.value === 'Go!') {
    num.value = Math.floor(Math.random() * 100)
    const countInt = parseInt(count.value*1000)
    intervalHandler = setInterval(() => {
      num.value = Math.floor(Math.random() * 100)
    }, countInt);
    state.value = 'Stop'
  } 
  else {
    state.value = 'Go!'
    clearInterval(intervalHandler)
  }
}

useForm({
  validationSchema: yup.object({
    count: yup.number().typeError('请输入数字').required().integer('请输入整数').max(1000_000, '已超过最大范围')
  })
})
const { value: count, errorMessage: countError } = useField('count')
const isValid = useIsFormValid()
</script>