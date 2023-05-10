<template>
  <h1 class="first-title">Dialog 示例</h1>

  <section class="second-title">
    <h2>基础用法</h2>
    <p>
      使用<span>v-model</span>绑定一个<span>Boolean</span>类型的变量到<span>Dialog</span>组件
    </p>
  </section>
  <Demo :component="Dialog1Demo"/>

  <section class="second-title">
    <h2>支持 bottomBtn</h2>
    <p>
      在<span>Dialog</span>组件中添加<span>bottomBtn</span>属性，以此来决定<span>Dialog</span>组件是否显示<span>处理button</span>
    </p>
  </section>
  <Demo :component="DialogBottom"/>

  <section class="second-title">
    <h2>利用TS打开 Dialog</h2>
    <p>引入<span>openDialog</span>模块创建一个<span>Dialog</span>组件</p>
  </section>
  <Demo :component="Dialog2Demo"/>
</template>

<script lang="ts">
import Demo from './Demo.vue'
import Dialog1Demo from './Dialog1.demo.vue'
import Dialog2Demo from './Dialog2.demo.vue'
import DialogBottom from './DialogBottom.vue'

export default {
  components: {Demo},
  setup() {
    return {Dialog1Demo, Dialog2Demo, DialogBottom}
  }
}
</script>