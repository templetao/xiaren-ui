<template>
  <div>
    <h1 class="first-title">Switch 组件示例</h1>
    <section class="second-title">
      <h2>基础用法</h2>
      <p>
        使用<span>v-model</span>绑定一个<span>Boolean</span>类型的变量到<span>Switch</span>组件
      </p>
    </section>
    <Demo :component="Switch1Demo"/>
    <section class="second-title">
      <h2>支持disabled属性</h2>
      <p>
        在<span>Switch</span>组件中添加<span>disabled</span>属性，以此来<span>禁用Switch</span>组件
      </p>
    </section>
    <Demo :component="Switch2Demo"/>
    <section class="second-title">
      <h2>支持loading属性</h2>
      <p>
        在<span>Switch</span>组件中添加<span>loading</span>属性，显示<span>Switch</span>组件加载状态
      </p>
    </section>
    <Demo :component="SwitchLoading"/>
  </div>
</template>
<script lang="ts">
import Switch1Demo from './Switch1Demo.vue'
import Switch2Demo from './Switch2Demo.vue'
import Demo from './Demo.vue'
import SwitchLoading from './SwitchLoading.vue'

export default {
  components: {Demo},
  setup() {
    return {Switch1Demo, Switch2Demo, SwitchLoading}
  },
}
</script>
<style lang="scss" scoped>
$border-color: #d9d9d9;
.demo {
  border: 1px solid $border-color;
  margin: 16px 0 32px;

  > h2 {
    font-size: 20px;
    padding: 8px 16px;
    border-bottom: 1px solid $border-color;
  }

  &-component {
    padding: 16px;
  }

  &-actions {
    padding: 8px 16px;
    border-top: 1px dashed $border-color;
  }

  &-code {
    padding: 8px 16px;
    border-top: 1px dashed $border-color;
    overflow: auto;

    > pre {
      line-height: 1.2;
      font-family: Consolas, "Courier New", Courier, monospace;
    }
  }
}
</style>