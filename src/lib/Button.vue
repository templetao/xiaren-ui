<template>
  <button class="xiaren-button" :class="classes" :disabled="disabled">
    <span v-if="loading" class="xiaren-loadingIndicator"></span>
    <slot></slot>
  </button>
</template>
<script lang="ts">
import {computed} from 'vue'

export default {
  props: {
    theme: {
      type: String,
      default: 'button',
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
    const {theme, size, level} = props
    const classes = computed(() => {
      return {
        [`xiaren-theme-${theme}`]: theme,
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
$border-color: #d9d9d9;
$color: #333;
$blue: #40a9ff;
$red: #f56c6c;
$radius: 4px;
$grey: #909399;
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
  //   相邻组件间相隔8px
  & + & {
    margin-left: 8px;
  }

  &:hover,
  &:focus {
    color: $blue;
    border-color: $blue;
  }

  &:focus {
    outline: none;
  }

  &::-moz-focus-inner {
    border: 0;
  }

  &.xiaren-theme-link {
    border-color: transparent;
    box-shadow: none;
    color: $blue;

    &:hover,
    &:focus {
      color: lighten($blue, 20%);
      text-decoration: underline;
    }
  }

  &.xiaren-theme-text {
    border-color: transparent;
    box-shadow: none;
    color: inherit;

    &:hover, &:focus {
      background: darken(white, 5%);
    }
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

  &.xiaren-theme-button {
    &.xiaren-level-main {
      background: $blue;
      color: white;
      border-color: $blue;

      &:hover, &:focus {
        background: darken($blue, 10%);
        border-color: darken($blue, 10%);
      }
    }

    &.xiaren-level-danger {
      background: $red;
      border-color: $red;
      color: white;

      &:hover, &:focus {
        background: darken($red, 10%);
        border-color: darken($red, 10%);
      }
    }
  }

  &.xiaren-theme-link {
    &.xiaren-level-danger {
      color: $red;

      &:hover, &:focus {
        color: darken($red, 10%);
      }
    }
  }

  &.xiaren-theme-text {
    &.xiaren-level-main {
      color: $blue;

      &:hover,
      &:focus {
        color: darken($blue, 10%);
      }
    }

    &.xiaren-level-danger {
      color: $red;

      &:hover,
      &:focus {
        color: darken($red, 10%);
      }
    }
  }

  &.xiaren-theme-button {
    &[disabled] {
      cursor: not-allowed;
      color: $grey;
      border-color: $grey;

      &:hover {
        border-color: $grey;
      }

    }
  }

  &.xiaren-theme-link, &.xiaren-theme-text {
    &[disabled] {
      cursor: not-allowed;
      color: $grey;

      &:hover {
        text-decoration: none;
        background-color: transparent;
      }
    }
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
