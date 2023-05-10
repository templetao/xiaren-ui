<demo>
支持 bottomBtn
</demo>

<template>
  <div>
    <Button level="error" @click="toggle">打开Dialog 有处理</Button>
    <Dialog v-model:visible="showDialog" bottomBtn
            :ok="confirm" :cancel="cancel"
    >
      <p>这是内容</p>
    </Dialog>
  </div>
</template>
<script lang="ts">
import Button from '../lib/Button.vue'
import Dialog from '../lib/Dialog.vue'
import {ref} from 'vue'

export default {
  components: {Dialog, Button},
  setup() {
    const showDialog = ref(false)
    const toggle = () => {
      showDialog.value = !showDialog.value
    }
    const confirm = () => {
      return true
    }
    const cancel = () => {
      return false
    }
    return {
      showDialog, toggle, confirm, cancel
    }
  }
}
</script>