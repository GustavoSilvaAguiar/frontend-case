<template>
  <div class="tabs">
    <div
      @click="tabSelector(tab), $emit('changeTab', tab)"
      class="tabs--btn"
      :class="currentTab !== tab.value ? 'inactive' : ''"
      v-for="(tab, index) in btnTabs"
      :key="index"
    >
      {{ tab.tab }}
    </div>
  </div>
</template>

<script lang="ts" setup>
import type { ITabs } from "@/Interfaces/tabs.ts";
interface IProps {
  btnTabs: ITabs[];
}
const props = defineProps<IProps>();
onMounted(() => {
  tabSelector(props.btnTabs[0]);
});
const currentTab = ref<string | number>();
const tabSelector = (tabValue: ITabs | undefined) => {
  currentTab.value = tabValue?.value;
  return tabValue;
};
</script>

<style lang="scss" scoped>
.tabs {
  overflow: auto;
  display: flex;
  padding: 4px;
  align-items: center;
  border-radius: 10px;
  column-gap: 4px;
  background: #f6f8fa;

  &--btn {
    text-align: center;
    cursor: pointer;
    width: 100%;
    padding: 4px;
    border-radius: 6px;
    background-color: #fff;
    box-shadow: 0px 2px 4px 0px rgba(27, 28, 29, 0.02),
      0px 6px 10px 0px rgba(27, 28, 29, 0.06);
  }

  .inactive {
    background-color: transparent !important;
    color: $light-gray;
    border: none;
    box-shadow: none;
  }
}
</style>
