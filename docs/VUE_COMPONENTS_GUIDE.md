# Vue 组件创建与引用指南

## 一、Vue 组件基础概念

### 1.1 什么是 Vue 组件？

Vue 组件是可复用的 Vue 实例，用于封装可重用的 UI 逻辑和模板。每个组件都有自己的：
- **模板 (Template)**: HTML 结构
- **脚本 (Script)**: JavaScript/TypeScript 逻辑
- **样式 (Style)**: CSS 样式（可选）

### 1.2 组件的作用

- **代码复用**: 一次编写，多处使用
- **模块化**: 将复杂 UI 拆分成独立模块
- **维护性**: 便于管理和更新

---

## 二、创建 Vue 组件

### 2.1 组件文件结构

在 Slidev 项目中，组件通常放在 `components/` 目录下，文件命名采用 **PascalCase**（如 `Counter.vue`）。

### 2.2 组件基本结构

```vue
<script setup lang="ts">
// 1. 导入 Vue API
import { ref, computed } from 'vue'

// 2. 定义 Props（组件接收的外部数据）
const props = defineProps({
  count: {
    type: Number,
    default: 0,
  },
})

// 3. 定义响应式数据
const counter = ref(props.count)

// 4. 定义计算属性（可选）
const doubled = computed(() => counter.value * 2)

// 5. 定义方法（可选）
function increment() {
  counter.value++
}
</script>

<template>
  <!-- HTML 模板 -->
  <div>
    <button @click="counter -= 1">-</button>
    <span>{{ counter }}</span>
    <button @click="counter += 1">+</button>
  </div>
</template>

<style scoped>
/* 样式（可选） */
/* scoped 表示样式只作用于当前组件 */
</style>
```

### 2.3 实际示例：Counter.vue

查看项目中的 `components/Counter.vue`：

```1:38:Web-mech/components/Counter.vue
<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps({
  count: {
    default: 0,
  },
})

const counter = ref(props.count)
</script>

<template>
  <div flex="~" w="min" border="~ main rounded-md">
    <button
      border="r main"
      p="2"
      font="mono"
      outline="!none"
      hover:bg="gray-400 opacity-20"
      @click="counter -= 1"
    >
      -
    </button>
    <span m="auto" p="2">{{ counter }}</span>
    <button
      border="l main"
      p="2"
      font="mono"
      outline="!none"
      hover:bg="gray-400 opacity-20"
      @click="counter += 1"
    >
      +
    </button>
  </div>
</template>
```

**关键点解析：**

1. **`<script setup>`**: Vue 3 的 Composition API 语法糖，更简洁
2. **`defineProps()`**: 定义组件接收的属性
3. **`ref()`**: 创建响应式数据
4. **`@click`**: 事件监听器（等同于 `v-on:click`）
5. **`{{ counter }}`**: 数据绑定（插值表达式）

---

## 三、在 Slidev 中引用组件

### 3.1 自动导入（推荐）

Slidev **自动导入** `components/` 目录下的所有 Vue 组件，无需手动导入！

**使用步骤：**

1. 在 `components/` 目录创建组件（如 `Counter.vue`）
2. 在 markdown 文件中直接使用组件标签

```markdown
<!-- 直接使用，无需导入 -->
<Counter :count="10" />
```

### 3.2 实际使用示例

查看 `example.md` 中的使用：

```280:285:Web-mech/example.md
```html
<Counter :count="10" />
```

<!-- ./components/Counter.vue -->
<Counter :count="10" m="t-4" />
```

### 3.3 Props 传递

**语法：**
```html
<!-- 传递字符串 -->
<MyComponent title="Hello" />

<!-- 传递数字（使用 v-bind 或 :） -->
<MyComponent :count="10" />

<!-- 传递布尔值 -->
<MyComponent :isActive="true" />

<!-- 传递对象 -->
<MyComponent :config="{ theme: 'dark' }" />
```

**示例：**
```markdown
<Counter :count="5" />
<Counter :count="20" />
```

---

## 四、创建自定义组件示例

### 4.1 创建一个简单的按钮组件

**创建文件：`components/CustomButton.vue`**

```vue
<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps({
  label: {
    type: String,
    default: 'Click me',
  },
  variant: {
    type: String,
    default: 'primary', // 'primary' | 'secondary' | 'danger'
  },
})

const emit = defineEmits(['click'])

function handleClick() {
  emit('click')
}
</script>

<template>
  <button
    :class="{
      'bg-blue-500': variant === 'primary',
      'bg-gray-500': variant === 'secondary',
      'bg-red-500': variant === 'danger',
    }"
    class="px-4 py-2 rounded text-white hover:opacity-80"
    @click="handleClick"
  >
    {{ label }}
  </button>
</template>
```

**在 markdown 中使用：**
```markdown
<CustomButton label="提交" variant="primary" />
<CustomButton label="取消" variant="secondary" />
<CustomButton label="删除" variant="danger" />
```

### 4.2 创建一个数据展示组件

**创建文件：`components/DataCard.vue`**

```vue
<script setup lang="ts">
const props = defineProps({
  title: String,
  value: [String, Number],
  unit: {
    type: String,
    default: '',
  },
})
</script>

<template>
  <div class="border rounded-lg p-4 shadow">
    <h3 class="text-sm text-gray-600 mb-2">{{ title }}</h3>
    <div class="text-2xl font-bold">
      {{ value }}<span class="text-sm ml-1">{{ unit }}</span>
    </div>
  </div>
</template>
```

**在 markdown 中使用：**
```markdown
<DataCard title="温度" :value="25" unit="°C" />
<DataCard title="湿度" :value="60" unit="%" />
```

---

## 五、组件通信

### 5.1 父组件 → 子组件：Props

```vue
<!-- 子组件 -->
<script setup>
defineProps({
  message: String
})
</script>

<template>
  <p>{{ message }}</p>
</template>
```

```markdown
<!-- 父组件（markdown） -->
<ChildComponent message="Hello from parent" />
```

### 5.2 子组件 → 父组件：Events

```vue
<!-- 子组件 -->
<script setup>
const emit = defineEmits(['update'])

function notify() {
  emit('update', 'New value')
}
</script>

<template>
  <button @click="notify">Notify Parent</button>
</template>
```

```markdown
<!-- 父组件（markdown） -->
<ChildComponent @update="handleUpdate" />

<script setup>
function handleUpdate(value) {
  console.log('Received:', value)
}
</script>
```

---

## 六、在 Markdown 中使用 Vue 特性

### 6.1 使用 Vue 指令

```markdown
<!-- v-if 条件渲染 -->
<div v-if="show">显示内容</div>

<!-- v-for 列表渲染 -->
<div v-for="item in items" :key="item.id">
  {{ item.name }}
</div>

<!-- v-click (Slidev 特有) -->
<div v-click>点击后显示</div>
<div v-click="2">第 2 步显示</div>
```

### 6.2 在 Markdown 中定义脚本

```markdown
<script setup lang="ts">
import { ref } from 'vue'

const count = ref(0)
const items = ref(['A', 'B', 'C'])
</script>

# 我的幻灯片

<Counter :count="count" />

<div v-for="item in items" :key="item">
  {{ item }}
</div>
```

---

## 七、最佳实践

### 7.1 组件命名

- ✅ **推荐**: `Counter.vue`, `DataCard.vue`, `CustomButton.vue`
- ❌ **避免**: `counter.vue`, `data-card.vue`（虽然可用，但不推荐）

### 7.2 Props 定义

```vue
<script setup>
// ✅ 推荐：明确类型和默认值
defineProps({
  title: {
    type: String,
    required: true,
  },
  count: {
    type: Number,
    default: 0,
  },
  isActive: {
    type: Boolean,
    default: false,
  },
})
</script>
```

### 7.3 组件组织

```
components/
  ├── Counter.vue          # 计数器组件
  ├── DataCard.vue          # 数据卡片
  ├── CustomButton.vue      # 自定义按钮
  └── charts/               # 图表组件目录
      ├── LineChart.vue
      └── BarChart.vue
```

### 7.4 样式作用域

```vue
<!-- ✅ 使用 scoped 避免样式污染 -->
<style scoped>
.my-class {
  color: red;
}
</style>

<!-- ✅ 或使用 CSS Modules -->
<style module>
.button {
  padding: 10px;
}
</style>
```

---

## 八、常见问题

### Q1: 组件不显示？

**检查清单：**
- ✅ 组件文件是否在 `components/` 目录下？
- ✅ 组件文件名是否为 PascalCase（如 `MyComponent.vue`）？
- ✅ 组件标签名是否正确（区分大小写）？
- ✅ 组件是否有语法错误（检查控制台）？

### Q2: Props 不生效？

- 确保使用 `:` 或 `v-bind` 传递非字符串值
- 检查 `defineProps` 中的属性名是否匹配

### Q3: 如何调试组件？

- 在组件中添加 `console.log()`
- 使用 Vue DevTools 浏览器扩展
- 检查浏览器控制台的错误信息

---

## 九、参考资源

- [Vue 3 官方文档](https://cn.vuejs.org/)
- [Slidev 组件文档](https://sli.dev/builtin/components.html)
- [Composition API 指南](https://cn.vuejs.org/guide/extras/composition-api-faq.html)

