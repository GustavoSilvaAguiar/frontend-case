<template>
  <div class="records">
    <div class="logo"><slot name="logo"></slot></div>

    <div>
      <div class="records--title"><slot></slot></div>
      <div>{{ time }}</div>
    </div>
    <img src="../../assets/icons/more-2-line.svg" />
  </div>
</template>

<script lang="ts" setup>
const props = defineProps<{ time: string }>();
</script>

<style lang="scss" scoped>
.records {
  display: grid;
  grid-template-columns: auto 1fr auto;
  gap: 10px;
  align-items: center;

  &--title {
    font-size: 14px;
    font-weight: 400;
    color: #0a0d14;
  }
  .logo {
    border-radius: 48px;
    border: 1px solid #e2e4e9;
    padding: 8px;
  }
}
</style>
