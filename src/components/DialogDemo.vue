<template>
  <div>Dialog 示例</div>
  <h1>示例 1</h1>
  <Button @click="toggle">toggle</Button>
  <Dialog v-model:visible="x" :closeOnClickOverlay="false"
          :ok="f1" :cancel="f2"
  >
    <template v-slot:content>
      <strong>hi</strong>
    </template>
    <template v-slot:title>
      <strong>加粗的标题</strong>
    </template>
  </Dialog>
</template>

<script setup lang="ts">
import Button from '../lib/Button.vue'
import Dialog from '../lib/Dialog.vue'
import {ref} from 'vue'

const x = ref(false)
const toggle = () => {
  x.value = !x.value
}
const f1 = () => {
  return false
}
const f2 = () => {}
</script>