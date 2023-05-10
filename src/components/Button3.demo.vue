<demo>
支持 round
</demo>
<template>
  <div>
    <div>
      <Button round>Click me</Button>
      <Button level="primary" round>Click me</Button>
      <Button level="success" round>Click me</Button>
      <Button level="warning" round>Click me</Button>
      <Button level="error" round>Click me</Button>
    </div>
  </div>
</template>

<script lang="ts">
import Button from '../lib/Button.vue'

export default {
  components: {
    Button
  }
}
</script>