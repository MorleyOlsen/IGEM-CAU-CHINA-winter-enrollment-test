<template>
  <div>
    <Nav />
    <div class="text-2xl font-bold m-8">
      欢迎来到第二个房间
    </div>
    <div class="font-bold">请在下面输入框中输入需要输出的随机数个数n！</div>
    <div>PS：随机数范围为0~100内的整数</div>
    <div class="text-sm text-red-400">
      {{ countError }}
    </div>
    <div class="mt-8 flex gap-2 justify-center">
      <input type="text" class="p-2 rounded-md bg-slate-100 dark:bg-zinc-700" v-model="count">
      <button @click="handleGo" :disabled="!isValid" class="disabled:opacity-50 disabled:cursor-not-allowed">
        Go！
      </button>
    </div>
    <div class="font-bold text-lg grid grid-cols-10 gap-2 mt-4 max-w-4xl truncate">
      <div v-for="num in nums">{{ num }}</div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { useField, useForm, useIsFormValid } from 'vee-validate'
import * as yup from 'yup'
import Nav from '../components/Nav.vue';

const nums = ref([])

const handleGo = () => {
  nums.value = []
  const countInt = parseInt(count.value)
  for (let i = 0; i < countInt; i++) {
    nums.value.push(Math.floor(Math.random() * 100))
  }
}

useForm({
  validationSchema: yup.object({
    count: yup.number().typeError('请输入数字').required().integer('请输入整数').max(1000_0, '已超过最大范围')
  })
})
const { value: count, errorMessage: countError } = useField('count')
const isValid = useIsFormValid()
</script>