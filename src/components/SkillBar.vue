<template>
  <div class="skill-bar">
    <div class="flex justify-between items-center mb-2">
      <span class="text-sm font-medium text-gray-700 dark:text-gray-300">{{ name }}</span>
      <span class="text-sm text-gray-500 dark:text-gray-400">{{ level }}%</span>
    </div>
    <div class="w-full bg-gray-200 dark:bg-dark-600 rounded-full h-2">
      <div 
        class="bg-gradient-to-r from-primary-500 to-primary-600 h-2 rounded-full transition-all duration-1000 ease-out"
        :style="{ width: isVisible ? `${level}%` : '0%' }"
      ></div>
    </div>
  </div>
</template>
<script setup>
import { ref, onMounted } from 'vue'
import { useIntersectionObserver } from '@vueuse/core'

defineProps({
  name: String,
  level: [String, Number]
})

const skillBar = ref(null)
const isVisible = ref(false)

onMounted(() => {
  const { stop } = useIntersectionObserver(
    skillBar,
    ([{ isIntersecting }]) => {
      if (isIntersecting) {
        setTimeout(() => {
          isVisible.value = true
        }, 200)
        stop()
      }
    },
    { threshold: 0.5 }
  )
})
</script>