<template>
  <div class="layout">
    <Topnav toggleMenuButtonVisible class="nav"/>
    <div class="content">
      <Aside/>
      <main>
        <router-view></router-view>
      </main>
    </div>
  </div>
</template>

<script lang="ts">
import Topnav from '../components/Topnav.vue'
import Aside from './Aside.vue'

export default {
  components: {Aside, Topnav},
}
</script>

<style lang="scss" scoped>
$aside-index: 10;

.layout {
  display: flex;
  flex-direction: column;
  height: 100vh;

  > .nav {
    flex-shrink: 0; //高度变化时不收缩
  }

  > .content {
    flex-grow: 1; //高度变化时占据剩余空间
    padding-top: 60px;
    padding-left: 180px;
    @media (max-width: 500px) {
      padding-top: 70px;
      padding-left: 0;
    }
  }
}

.content {
  position: relative;
  display: flex;
  flex-direction: column;

  > aside {
    flex-shrink: 0; //宽度变化时不收缩
  }

  > main {
    flex-grow: 1; //宽度变化时占据剩余空间
    padding: 60px;
    background-color: #fff;
    @media (max-width: 500px) {
      padding: 60px 30px;
    }
  }
}

main {
  height: 100vh;
  overflow: auto;
}
</style>