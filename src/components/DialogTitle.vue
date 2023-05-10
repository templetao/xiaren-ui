<demo>
支持 title
</demo>
<template>
  <div>
    <Button level="primary" @click="toggle"> 打开Dialog有标题</Button>
    <Dialog v-model:visible="showDialog" title="自定义标题">
      <p>这是内容</p>
    </Dialog>
  </div>
</template>

<script lang="ts">
import Button from '../lib/Button.vue'
import Dialog from '../lib/Dialog.vue'
import {ref} from 'vue'

export default {
  components: {Dialog, Button,},
  setup() {
    const showDialog = ref(false)
    const toggle = () => {
      showDialog.value = !showDialog.value
    }
    return {showDialog, toggle,}
  },
}
</script>