<template>
  <div class="sideBar--btn">
    <div
      class="sideBar--btn--indicator"
      :class="pageSelected(url) ? 'sideBar--btn--indicator--selected' : ''"
    />
    <NuxtLink
      :to="url"
      class="sideBar--btn--btnBody"
      :class="[pageSelected(url) ? 'sideBar--btn--btnBody--selecionado' : '', closed ? 'sideBar--btn--btnBodyClosed' : '']"
    >
      <slot class="icon"></slot>
      <!-- <groupIconVue class="icon" /> -->
      <span :class="closed ? 'closed' : ''">{{ title }}</span>

      <img
        :class="closed ? 'closed' : ''"
        src="../../assets/icons/arrow-right-s-line.svg"
      />
    </NuxtLink>
  </div>
</template>

<script lang="ts" setup>
defineProps<{ url: string; title: string; closed: boolean }>();

const route = useRoute();

const pageSelected = (rota: string) => {
  switch (route.fullPath) {
    case rota:
      return true;
    default:
      return false;
  }
};
</script>

<style lang="scss" scoped>
.closed {
  display: none !important;
}

.sideBar {
  &--btn {
    display: flex;
    align-items: center;

    &--indicator {
      width: 4px;
      height: 20px;
      border-radius: 0px 4px 4px 0px;
      background: $primary;
      display: none;

      &--selected,
      &:hover {
        display: block;
      }
    }

    &--btnBody {
      width: 100%;
      text-decoration: none;
      display: grid;
      grid-template-columns: auto 1fr auto;
      padding: 8px 12px;
      align-items: center;
      gap: 8px;
      color: #525866;
      font-weight: 500;
      font-size: 14px;
      margin-left: 20px;
      margin-right: 20px;
      transition: all 0.2s;
      img {
        display: none;
      }

      &:hover,
      &--selecionado {
        color: #0a0d14;
        border-radius: 8px;
        background-color: #f6f8fa;
        margin-left: 16px;
        img {
          display: block;
        }
        .yy {
          fill: $primary;
        }
      }
    }

    &--btnBodyClosed {
      display: flex ;
      justify-content: center;
      margin: 0;
    }
  }
}
</style>
