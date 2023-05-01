<template>
  <div>
    <Switch v-model:value="y"/>
  </div>
</template>
<script setup lang="ts">
import Switch from '../../lib/Switch.vue'
import {ref} from 'vue'

const y = ref(false)

</script>