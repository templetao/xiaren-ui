<template>
  <transition name="slide">
    <aside v-show="menuVisible">
      <h2>文档</h2>
      <ol>
        <li>
          <router-link to="/doc/intro">介绍</router-link>
        </li>
        <li>
          <router-link to="/doc/install">安装</router-link>
        </li>
        <li>
          <router-link to="/doc/get-started">开始使用</router-link>
        </li>
      </ol>
      <h2>组件列表</h2>
      <ol>
        <li>
          <router-link to="/doc/switch">Switch 组件</router-link>
        </li>
        <li>
          <router-link to="/doc/button">Button 组件</router-link>
        </li>
        <li>
          <router-link to="/doc/dialog">Dialog 组件</router-link>
        </li>
        <li>
          <router-link to="/doc/tabs">Tabs 组件</router-link>
        </li>
      </ol>
    </aside>
  </transition>
</template>
<script lang="ts">
import {inject, Ref} from 'vue'

export default {
  setup() {
    const menuVisible = inject<Ref<boolean>>('menuVisible')
    return {menuVisible}
  },
}
</script>
<style lang="scss">
$light-bgc: #709acb;
$deep-bgc: #44295b;
$text: #6f2e6a;
aside {
  position: absolute;
  top: 0;
  left: 0;
  width: 200px;
  height: 100%;
  // font-size: 18px;
  padding: 80px 0 16px;
  background: #fff;
  box-shadow: 5px 0 5px rgba(#333, 0.1);
  z-index: 1;
  transition: all 0.4s cubic-bezier(0.7, 0.2, 0.5, 0.2) 0.1s;

  > h2 {
    margin-bottom: 4px;
    margin-top: 16px;
    padding: 0 40px;
  }

  > ol {
    line-height: 40px;

    > li {
      > a {
        position: relative;
        height: 40px;
        color: $text;
        display: block;
        padding: 4px 50px;
        text-decoration: none;

        &:hover {
          color: #fff;
          background: $light-bgc;
          border-bottom: none;
        }
      }

      .router-link-active {
        background: $light-bgc;
        color: #fff;
        border-right: 3px solid $deep-bgc;
        @media (min-width: 500px) {
          border-right: none;
          &::after {
            content: "";
            display: block;
            animation: bdrolate 0.8s;
            position: absolute;
            top: 0;
            right: 0;
            width: 3px;
            height: 40px;
            background-color: $deep-bgc;
          }
        }
      }
    }
  }

  @keyframes bdrolate {
    0% {
      transform: rotateX(90deg);
    }
    100% {
      transform: rotateX(0deg);
    }
  }
}
</style>