<template>
  <div class="xiaren-tabs">
    <div class="xiaren-tabs-nav" ref="container">
      <div class="xiaren-tabs-nav-item"
           v-for="(itemTitle, index) in titles"
           :ref="(el) => {
             if(itemTitle === selected) selected = el;
           }"
           @click="select(itemTitle)"
           :class="{selected: itemTitle === selected}"
           :key="index"
      >
        {{ itemTitle }}
      </div>
      <div class="xiaren-tabs-nav-indicator"></div>
    </div>
    <div class="xiaren-tabs-content">
      <component class="xiaren-tabs-content-item"
                 :key="current.props.title" :is="current"
      />
    </div>
  </div>
</template>

<script lang="ts" setup>
import {computed, onMounted, ref, useSlots, watchEffect} from 'vue'
import Tab from './Tab.vue'

const props = defineProps({
  selected: String,
})
const slots = useSlots()
const emit = defineEmits(['update:selected'])

const selectedItem = ref<HTMLDivElement>(null)
const indicator = ref<HTMLDivElement>(null)
const container = ref<HTMLDivElement>(null)

// const x = () => {
//   const { width } = selectedItem.value.getBoundingClientRect();
//   indicator.value.style.width = width + "px";
//   const { left: left1 } = container.value.getBoundingClientRect();
//   const { left: left2 } = selectedItem.value.getBoundingClientRect();
//   const left = left2 - left1;
//   indicator.value.style.left = left + "px";
// };
onMounted(() => {
  watchEffect(() => {
    const {width} = selectedItem.value.getBoundingClientRect()
    console.log(selectedItem.value)
    indicator.value.style.width = width + 'px'
    const {left: left1} = container.value.getBoundingClientRect()
    const {left: left2} = selectedItem.value.getBoundingClientRect()
    const left = left2 - left1
    console.log(left)
    indicator.value.style.left = left + 'px'
  })
})
// onMounted(x);
// onUpdated(x);

const defaults = slots.default()
if (!slots.default) {
  throw new Error('Tabs 必须至少包含一个 Tab')
}
defaults.forEach((tag) => {
  if (tag.type !== Tab) {
    throw new Error('Tabs 子标签必须是 Tab')
  }
})

const current = computed(() => {
  return defaults.find((tag) => tag.props.title)
})

const titles = defaults.map((tag) => {
  return tag.props.title
})

const select = (title: String) => {
  emit('update:selected', title)
}
</script>

<style lang="scss" scoped>
$blue: #40a9ff;
$color: #333;
$border-color: #d9d9d9;

.xiaren-tabs {
  &-nav {
    display: flex;
    color: $color;
    border-bottom: 1px solid $border-color;
    position: relative;

    &-item {
      padding: 8px 0;
      margin: 0 16px;
      cursor: pointer;

      &:first-child {
        margin-left: 0;
      }

      &.selected {
        color: $blue;
      }
    }

    &-indicator {
      position: absolute;
      height: 4px;
      background: $blue;
      left: 0;
      bottom: -2px;
      transition: all 250ms;
    }
  }

  &-content {
    padding: 8px 0;
  }
}
</style>