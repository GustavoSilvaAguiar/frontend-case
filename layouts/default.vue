<template>
  <div class="wrap">
    <LayoutSideBar />
    <div class="wrap--rightSide">
      <LayoutHeader />
      <div class="slot"><slot></slot></div>
    </div>
  </div>
</template>

<script setup></script>

<style lang="scss" scoped>
.wrap {
  display: flex;
  height: 100vh;
  width: 100vw;

  &--rightSide {
    display: grid;
    grid-template-rows: auto 1fr;
    width: 100%;
    height: 100%;
  }
  .slot {
    width: 100%;
    height: 100%;
    overflow: auto;
  }
}
</style>
