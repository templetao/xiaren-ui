<template>
  <h1 class="first-title">Tabs 示例</h1>
  <section class="second-title">
    <h2>基础用法</h2>
    <p>
      使用<span>v-model</span>绑定一个<span>Boolean</span>类型的变量到<span>Tabs</span>组件,指定默认<span>Tab</span>
    </p>
  </section>
  <Demo :component="Tabs1Demo"/>
</template>

<script lang="ts">
import Demo from './Demo.vue'
import Tabs1Demo from './Tabs1.demo.vue'

export default {
  components: {Demo},
  setup() {
    return {Tabs1Demo}
  },
}
</script>