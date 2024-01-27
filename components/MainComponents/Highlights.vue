<template>
  <div class="highlights">
    <div class="highlights--header">
      <starSmileIconVue />Destaque colaboradores<CommonBtn
        ><template #icon
          ><img src="../../assets/icons/share-forward-line.svg"
        /></template>
        Enviar</CommonBtn
      >
    </div>
    <CommonTabs :btn-tabs="tabs" @changeTab="changeTab" />
    <HighlightsComponentsTabGeralEPremios v-if="showTab(1)" />
    <HighlightsComponentsTabComentarios v-if="showTab(2)" />
    <HighlightsComponentsTabGeralEPremios tab-premios v-if="showTab(3)" />
  </div>
</template>

<script lang="ts" setup>
import type { ITabs } from "~/Interfaces/tabs";
import starSmileIconVue from "~/assets/icons/starSmileIcon.vue";

const tabs = [
  { tab: "Geral", value: 1 },
  { tab: "Comentários", value: 2 },
  { tab: "Prêmios", value: 3 },
] as ITabs[];

const currentTab = ref<ITabs>(tabs[0]);
const changeTab = (tab: ITabs) => {
  currentTab.value = tab;
};

const showTab = (tabValue: string | number) => {
  switch (currentTab.value?.value) {
    case tabValue:
      return true;
    case tabValue:
      return true;
    case tabValue:
      return true;

    default:
      break;
  }
};
</script>

<style lang="scss" scoped>
.highlights {
  display: flex;
  flex-direction: column;
  row-gap: 16px;
  border-radius: 16px;
  padding: 16px;
  border: 1px solid #e2e4e9;
  box-shadow: 0px 1px 2px 0px rgba(228, 229, 231, 0.24);
  width: calc(100% - 32px);
  height: calc(100% - 32px);

  &--header {
    display: grid;
    align-items: center;
    grid-template-columns: auto 1fr auto;
    gap: 8px;
    font-size: 16px;
    font-weight: 500;
    color: #0a0d14;
  }
  &--main {
    display: flex;
    flex-direction: column;
    justify-content: space-between;

    &--text {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 4px;

      &--title {
        color: #0a0d14;
        font-size: 20px;
        font-weight: 700;
      }
      &--subtitle {
        color: #525866;
        font-size: 14px;
        font-weight: 400;
      }
    }

    &--footer {
      color: #525866;
      font-size: 14px;
      font-weight: 400;
    }

    &--img {
      position: relative;
      margin-bottom: 20px;
      margin-left: auto;
      margin-right: auto;

      &--avatar {
        position: absolute;
        left: 108px;
        top: 33px;
      }
    }
  }
}
</style>
