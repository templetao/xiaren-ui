<template>
  <div>
    <Topnav/>
    <div class="topnavAndBanner">
      <Topnav/>
      <div class="banner">
        <h1>xiaren-UI</h1>
        <h2>一个厉害的UI框架</h2>
        <p class="actions">
          <a href="https://github.com/templetao">github</a>
          <router-link to="/doc">开始</router-link>
        </p>
      </div>
    </div>
    <div class="features">
      <svg class="icon">
        <use xlink:href="#icon-vue"></use>
      </svg>
      <svg class="icon">
        <use xlink:href="#icon-ts"></use>
      </svg>
      <svg class="icon">
        <use xlink:href="#icon-read"></use>
      </svg>
    </div>
  </div>
</template>
<script lang="ts" setup>
import Topnav from '../components/Topnav.vue'

</script>

<style lang="scss" scoped>
.topnavAndBanner {
  background: linear-gradient(
    145deg,
    rgba(174, 238, 190, 1) 0%,
    rgba(148, 187, 233, 1) 100%);
  clip-path: ellipse(80% 60% at 50% 40%);
}

.features {
  > svg {
    width: 64px;
    height: 64px;
  }
}

.banner {
  padding: 100px 0;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;

  > .actions {
    padding: 8px 0;
    color: white;
    outline: none;

    a {
      margin: 0 8px;
      background: #02bcb0;
      $h: 28px;
      height: $h;
      line-height: $h;
      border-radius: calc($h / 2);
      padding: 4px 8px;
    }
  }
}
</style>