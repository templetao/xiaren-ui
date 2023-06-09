<template>
  <button class="xiaren-button" :class="classes"
          :disabled="loading ? true : disabled">
    <span v-if="loading" class="xiaren-loadingIndicator"></span>
    <slot></slot>
  </button>
</template>
<script lang="ts">
import {computed} from 'vue'

export default {
  props: {
    round: {
      type: Boolean,
      default: false,
    },
    size: {
      type: String,
      default: 'normal',
    },
    level: {
      type: String,
      default: 'normal',
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    loading: {
      type: Boolean,
      default: false,
    },
  },

  setup(props) {
    const {round, size, level} = props
    const classes = computed(() => {
      return {
        [`xiaren-${round ? 'round' : 'normal'}`]: round,
        [`xiaren-size-${size}`]: size,
        [`xiaren-level-${level}`]: level,
      }
    })
    return {classes}
  },
}
</script>
<style lang="scss">
$h: 32px;
$border-color: #333;
$color: #333;
$blue: #40a9ff;
$red: #f56c6c;
$radius: 4px;
$grey: #909399;
$roundRadius: 32px;

.xiaren-button {
  box-sizing: border-box;
  height: $h;
  padding: 0 12px;
  cursor: pointer;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  //   文本不换行显示
  white-space: nowrap;
  background: white;
  color: $color;
  border: 1px solid $border-color;
  border-radius: $radius;
  box-shadow: 0 1px 0 fade-out(black, 0.95);
  transition: background 0.25s;
  margin: 0 10px 8px 0;

  @media (min-width: 500px) {
    &:hover {
      animation: button-hover 0.5s linear forwards;
      &[disabled] {
        animation: none;
      }
    }
  }

  &:focus {
    color: $blue;
    border-color: $blue;
    box-shadow: 0 0 10px #ccc;
    outline: none;
  }

  &::-moz-focus-inner {
    border: 0;
  }

  &.xiaren-round {
    border-radius: $roundRadius;
  }

  &[disabled] {
    cursor: not-allowed;
    color: #fff;
    background-color: #ddd;
    border: none;
  }

  &.xiaren-size-big {
    font-size: 24px;
    height: 48px;
    padding: 0 16px;
  }

  &.xiaren-size-small {
    font-size: 12px;
    height: 20px;
    padding: 0 4px;
  }

  &.xiaren-level-primary {
    color: #fff;
    border: none;
    background-color: #1976d2;
  }

  &.xiaren-level-success {
    color: #fff;
    border: none;
    background-color: #13ce66;
  }

  &.xiaren-level-warning {
    color: #fff;
    border: none;
    background-color: #ffc107;
  }

  &.xiaren-level-error {
    color: #fff;
    border: none;
    background-color: #ff4f57;
  }

  > .xiaren-loadingIndicator {
    width: 14px;
    height: 14px;
    display: inline-block;
    margin-right: 4px;
    border-radius: 8px;
    border-color: lighten($blue, 20%) lighten($blue, 10%) $blue transparent;
    border-style: solid;
    border-width: 2px;
    animation: xiaren-spin 1s infinite linear;
  }
}
</style>
