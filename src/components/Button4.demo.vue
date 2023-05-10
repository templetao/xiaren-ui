<demo>
支持 disabled
</demo>
<template>
  <Button size="big" disabled>不能点击</Button>
  <Button round disabled>不能点击</Button>
  <Button size="small" disabled>不能点击</Button>
</template>

<script lang="ts">
import Button from '../lib/Button.vue'

export default {
  components: {
    Button
  }
}
</script>