<template>
  <div>
    <button @click="toggle" :class="{ checked: value }"><span>Switch</span></button>
  </div>
</template>

<script setup lang="ts">

const props = defineProps({
  value: Boolean
})

const emit = defineEmits(['input'])

const toggle = () => {
  emit('input', !props.value)
}
</script>

<style lang="scss">
$h: 22px;
$h2: calc($h - 4px);
button {
  position: relative;
  display: inline-block;
  width: $h * 2;
  height: $h;
  vertical-align: middle;
  border: none;
  background: #bfbfbf; // #1890ff
  border-radius: calc($h * 2);
  outline: none;
  cursor: pointer;
  transition: all 250ms;

  > span {
    position: absolute;
    top: 2px;
    left: 2px;
    width: $h2;
    height: $h2;
    border: none;
    border-radius: calc($h / 2);
    background: #fff;
  }
}

button.checked {
  background-color: #1890ff;

  > span {
    left: calc(100% - #{$h2} - 2px);
  }
}
</style>