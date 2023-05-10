<demo>
基础使用
</demo>
<template>
  <div>
    <Button>Click me</Button>
    <Button level="primary">Click me</Button>
    <Button level="success">Click me</Button>
    <Button level="warning">Click me</Button>
    <Button level="error">Click me</Button>
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