<template>
  <div>
    <button @click="toggle" :class="{ checked: value }"><span>Switch</span></button>
  </div>
</template>

<script setup lang="ts">

const props = defineProps({
  value: Boolean
})

const emit = defineEmits(['update:value'])

const toggle = () => {
  emit('update:value', !props.value)
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

  &:focus {
    box-shadow: 0 0 10px rgba(191, 191, 191, 0.7);
  }

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

  &:active {
    box-shadow: none;

    > span {
      width: calc($h + 2px);
    }
  }
}

button.checked {
  background-color: #1890ff;

  > span {
    left: calc(100% - #{$h2} - 2px);
  }

  &:focus {
    box-shadow: 0 0 10px rgba(24, 144, 255, 0.7);
  }

  &:active {
    box-shadow: none;

    > span {
      width: calc($h + 2px);
      margin-left: -6px;
    }
  }
}
</style>