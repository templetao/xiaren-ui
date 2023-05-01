<template>
  <div>
    <button><span>xx</span></button>
  </div>
</template>
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
  background: #1890ff;
  border-radius: calc($h * 2);
  outline: none;
  cursor: pointer;
  transition: all 0.2s;
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
</style>