<script setup lang="ts">
import { ref, computed } from 'vue'

// 定义 Props
const props = defineProps({
  name: {
    type: String,
    default: 'World',
  },
  initialCount: {
    type: Number,
    default: 0,
  },
})

// 响应式数据
const count = ref(props.initialCount)

// 计算属性
const greeting = computed(() => `Hello, ${props.name}!`)

// 方法
function increment() {
  count.value++
}

function decrement() {
  count.value--
}

function reset() {
  count.value = props.initialCount
}
</script>

<template>
  <div class="hello-world">
    <h3 class="text-xl font-bold mb-4">{{ greeting }}</h3>
    
    <div class="flex items-center gap-4 mb-4">
      <button
        class="px-4 py-2 bg-red-500 text-white rounded hover:bg-red-600"
        @click="decrement"
      >
        -
      </button>
      
      <span class="text-2xl font-mono min-w-[60px] text-center">
        {{ count }}
      </span>
      
      <button
        class="px-4 py-2 bg-green-500 text-white rounded hover:bg-green-600"
        @click="increment"
      >
        +
      </button>
    </div>
    
    <button
      class="px-4 py-2 bg-gray-500 text-white rounded hover:bg-gray-600 text-sm"
      @click="reset"
    >
      重置
    </button>
  </div>
</template>

<style scoped>
.hello-world {
  padding: 1rem;
  border: 2px solid #e5e7eb;
  border-radius: 0.5rem;
  background: #f9fafb;
}
</style>

