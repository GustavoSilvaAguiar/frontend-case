<template>
  <progress :value="value" :max="max"></progress>
</template>

<script lang="ts" setup>
defineProps({
    max: Number,
    value: Number
})
</script>

<style lang="scss" scoped>
progress {
  height: 8px;
}
progress[value] {
  appearance: none;
  background-color: #eee;
  border: none;
  border-radius: 5px;
}
progress[value]::-webkit-progress-bar {
  background-color: #eee;
  border-radius: 5px;
}
progress[value]::-webkit-progress-value {
  /* Altere a cor da parte preenchida da barra de progresso aqui */
  background-color: $primary;
  border-radius: 5px;
}
progress[value]::-moz-progress-bar {
  /* Altere a cor da parte preenchida da barra de progresso aqui */
  background-color: $primary;
  border-radius: 5px;
}
</style>
