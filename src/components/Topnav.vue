<template>
  <div class="topnav">
    <span class="toggleAside" @click="toggleMenu">LOGO</span>
    <ul class="menu">
      <li>菜单1</li>
      <li>菜单2</li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import {inject, Ref} from 'vue'

const menuVisible = inject<Ref<boolean>>('menuVisible') // get
const toggleMenu = () => {
  menuVisible.value = !menuVisible.value
}
</script>

<style lang="scss" scoped>
.topnav {
  background-color: pink;
  display: flex;
  padding: 16px;
  justify-content: center;
  align-items: center;

  > .logo {
    max-width: 6em;
    margin-right: auto;
  }

  > .menu {
    display: flex;
    flex-direction: row;
    white-space: nowrap;
    flex-wrap: nowrap;

    > li {
      margin: 10px 1em;
    }
  }

  > .toggleAside {
  }

  @media (max-width: 500px) {
    > .menu {
      display: none;
    }
    > .logo {
      margin: 0 auto;
    }
  }
}
</style>