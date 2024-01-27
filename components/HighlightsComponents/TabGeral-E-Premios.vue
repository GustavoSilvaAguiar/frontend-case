<template>
  <div class="main">
    <div class="main--text">
      <div class="main--text--title">
        {{ tabPremios ? "Cartão presente de R$ 50,00" : "Matthew Johnson" }}
      </div>
      <div class="main--text--subtitle">
        {{
          tabPremios ? "Aproveite o prêmio, Matthew!" : "Engenheiro de Software"
        }}
      </div>
    </div>
    <div class="main--img">
      <img src="../../assets/images/highlightsImage.svg" />
      <img
        v-if="!tabPremios"
        class="main--img--avatar"
        src="../../assets/images/avatar2.svg"
      />
      <img
        v-if="tabPremios"
        class="main--img--avatar"
        src="../../assets/icons/presente.svg"
      />
    </div>
    <div class="main--footer">
      {{
        tabPremios
          ? "Os funcionários do mês recebem recompensas"
          : "Funcionário de melhor desempenho de dezembro!"
      }}
    </div>
  </div>
</template>

<script lang="ts" setup>
interface IProps {
  tabPremios?: boolean;
}
defineProps<IProps>();
</script>

<style lang="scss" scoped>
.main {
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
    text-align: center;
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
</style>
