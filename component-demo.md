---
theme: seriph
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
transition: slide-left
---

# Vue 组件演示

组件创建与引用示例

<div class="pt-12">
  <span class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    按空格键继续 <carbon:arrow-right class="inline"/>
  </span>
</div>

---

# 1. 使用 Counter 组件

这是项目自带的 Counter 组件：

```html
<Counter :count="10" />
```

<Counter :count="10" m="t-4" />

---

# 2. 使用 HelloWorld 组件

这是新创建的 HelloWorld 组件：

```html
<HelloWorld name="Slidev" :initialCount="5" />
```

<HelloWorld name="Slidev" :initialCount="5" />

---

# 3. 多个组件实例

可以创建多个独立的组件实例：

<div class="grid grid-cols-2 gap-4">
  <div>
    <h4>实例 1</h4>
    <HelloWorld name="Alice" :initialCount="0" />
  </div>
  <div>
    <h4>实例 2</h4>
    <HelloWorld name="Bob" :initialCount="10" />
  </div>
</div>

---

# 4. 在 Markdown 中使用 Vue 脚本

你可以在 markdown 中定义数据，然后传递给组件：

<script setup lang="ts">
import { ref } from 'vue'

const dynamicCount = ref(15)
const userName = ref('Vue 开发者')
</script>

<div class="mb-4">
  <p>动态数据：{{ dynamicCount }}</p>
  <p>用户名：{{ userName }}</p>
</div>

<HelloWorld :name="userName" :initialCount="dynamicCount" />

---

# 5. 组件组合使用

多个组件可以组合在一起：

<div class="grid grid-cols-2 gap-4">
  <div>
    <h4 class="mb-2">计数器 1</h4>
    <Counter :count="5" />
  </div>
  <div>
    <h4 class="mb-2">计数器 2</h4>
    <Counter :count="20" />
  </div>
</div>

<div class="mt-4">
  <h4 class="mb-2">HelloWorld 组件</h4>
  <HelloWorld name="组合示例" :initialCount="0" />
</div>

---

# 总结

✅ **创建组件**: 在 `components/` 目录下创建 `.vue` 文件

✅ **自动导入**: Slidev 自动导入所有组件，无需手动导入

✅ **使用组件**: 直接在 markdown 中使用 `<ComponentName />`

✅ **传递 Props**: 使用 `:propName="value"` 传递数据

✅ **组合使用**: 可以在 markdown 中定义脚本和数据

---

# 下一步

查看 `VUE_COMPONENTS_GUIDE.md` 了解更多详情！

