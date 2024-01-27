<template>
  <div class="dailyWork">
    <div class="dailyWork--header">
      <ClockIcon />Horas diárias de trabalho<CommonBtn>Detalhes</CommonBtn>
    </div>
    <div class="divider" />
    <div class="dailyWork--text">
      <strong>12</strong> horas <strong>27</strong> minutos no total ⏳
    </div>
    <div class="dailyWork--bar">
      <div class="dailyWork--bar--descanso" />
      <div class="dailyWork--bar--ativo" />
      <div class="dailyWork--bar--extra" />
    </div>
    <div class="dailyWork--subtitle">
      <div
        v-for="(sub, index) in subtitle"
        :key="index"
        class="dailyWork--subtitle--sub"
      >
        <div
          :style="`width: 8px; height: 8px; border-radius: 100%; background-color: ${sub.color}`"
        />
        {{ sub.subtitle }}
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import ClockIcon from "~/assets/icons/clockIcon.vue";

const subtitle = [
  { subtitle: "Descanso", color: "#F2AE40" },
  { subtitle: "Ativo", color: "#35B9E9" },
  { subtitle: "Hora extra", color: "#6E3FF3" },
];
</script>

<style lang="scss" scoped>
.dailyWork {
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

  &--text {
    color: #525866;
    font-weight: 400;

    strong {
      color: #0a0d14;
      font-weight: 700;
    }
  }

  &--bar {
    display: flex;
    align-items: center;
    column-gap: 6px;

    &--descanso {
      height: 10px;
      width: 25%;
      border-radius: 2px;
      background: #f2ae40;
    }
    &--ativo {
      height: 10px;
      width: 60%;
      border-radius: 2px;
      background: #35b9e9;
    }
    &--extra {
      height: 10px;
      width: 15%;
      border-radius: 2px;
      background: #6e3ff3;
    }
  }

  &--subtitle {
    font-size: 12px;
    font-weight: 400;
    display: flex;
    align-items: center;
    column-gap: 16px;
    &--sub {
      display: flex;
      align-items: center;
      column-gap: 4px;
    }
  }
}
.divider {
  height: 1px;
  background: #e2e4e9;
}
</style>
