<template>
  <div>
    <Switch v-model:value="flag"/>
  </div>
</template>
<script setup lang="ts">
import Switch from '../../lib/Switch.vue'
import {ref} from 'vue'

const flag = ref(false)

</script>