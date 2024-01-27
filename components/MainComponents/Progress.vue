<template>
  <div class="progress">
    <div class="progress--header">
      <ClockIcon />Cursos - Progresso<CommonBtn>Ver todos</CommonBtn>
    </div>
    <div class="divider" />
    <div class="progress--main">
      <ProgressComponentsProgressCircle :porcentagem="90" />
      <div class="progress--main--text">
        <span>Diversidade da equipe</span>
        <p>Projetado para promover a inclusividade e perspectivas diversas.</p>
        <div>Retomar curso</div>
      </div>
    </div>
  </div>
</template>

<script setup>
import ClockIcon from "~/assets/icons/clockIcon.vue";
</script>

<style lang="scss" scoped>
.progress {
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
    align-items: center;
    column-gap: 20px;

    &--text {
      display: flex;
      flex-direction: column;
      font-size: 12px;
      font-weight: 400;
      color: #525866;

      span {
        color: #0a0d14;
        font-size: 14px;
        font-weight: 600;
      }
      div {
        color: $primary;
        font-size: 12px;
        font-weight: 500;
        text-decoration-line: underline;
        cursor: pointer;
      }
    }
  }
}

.divider {
  height: 1px;
  background: #e2e4e9;
}
</style>
