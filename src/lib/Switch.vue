<template>
  <div>
    <button class="xiaren-switch"
            @click="toggle"
            :class="{'xiaren-checked': value}">
      <span></span>
      <p v-if="!value">0</p>
      <p v-else>1</p>
    </button>
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
.xiaren-switch {
  position: relative;
  display: inline-block;
  width: $h * 2;
  height: $h;
  vertical-align: middle;
  border: none;
  margin-bottom: 8px;
  background: #bfbfbf; // #1890ff
  border-radius: calc($h * 2);
  outline: none;
  cursor: pointer;
  transition: all 250ms ease-in-out;

  &:focus {
    box-shadow: 0 0 10px rgba(191, 191, 191, 0.5);
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
    transition: all 250ms ease-in-out;
  }

  > p {
    display: inline-block;
    width: 12px;
    height: $h;
    font-size: 12px;
    color: #fff;
    margin: 0 8px 0 24px;
    transition: all 250ms ease-in-out;
  }

  &:active {
    box-shadow: none;

    > span {
      width: calc($h + 2px);
    }
  }
}

.xiaren-switch.xiaren-checked {
  background-color: #1890ff;

  > span {
    left: calc(100% - #{$h2} - 2px);
  }

  > p {
    margin: 0 8px 0 24px;
  }

  &:focus {
    box-shadow: 0 0 10px rgba(24, 144, 255, 0.5);
    &:hover {
      box-shadow: none;
    }
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