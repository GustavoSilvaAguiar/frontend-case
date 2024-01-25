<template>
  <div class="headerWrap">
    <div class="headerWrap--account">
      <img src="../../assets/images/Avatar.png" height="40px" width="40px" />
      <div class="headerWrap--account--text">
        <span class="headerWrap--account--text--name">Sophia Williams</span>
        <span class="headerWrap--account--text--msg"
          >Bem-vinda de volta 👋🏻</span
        >
      </div>
    </div>
    <div class="headerWrap--functions">
      <img src="../../assets/icons/search-2-line.svg" />
      <img src="../../assets/icons/notificationBell.svg" />
      <CommonBtn>
        <template #icon> <CalendarIcon class="icon" /> </template>Calendário
      </CommonBtn>
      <CommonBtn btn-color="primary">
        <template #icon> <PlusIcon class="icon" /> </template>Nova solicitação
      </CommonBtn>
    </div>
  </div>
</template>

<script setup>
import CalendarIcon from "~/assets/icons/calendarIcon.vue";
import PlusIcon from "~/assets/icons/plusIcon.vue";
</script>

<style lang="scss" scoped>
.headerWrap {
  display: flex;
  padding: 0px 32px;
  justify-content: space-between;
  align-items: center;
  height: 64px;

  &--account {
    display: flex;
    align-items: center;
    column-gap: 14px;

    &--text {
      display: flex;
      flex-direction: column;

      &--name {
        font-size: 18px;
        font-weight: 500;
        color: #0a0d14;
      }
      &--msg {
        font-size: 14px;
        font-weight: 400;
        color: #525866;
      }
    }
  }

  &--functions {
    display: flex;
    align-items: center;
    column-gap: 12px;
  }
}
@media screen and (max-width: 768px) {
  .headerWrap {
    justify-content: right;
    &--account {
      display: none;
    }
  }
}
</style>
