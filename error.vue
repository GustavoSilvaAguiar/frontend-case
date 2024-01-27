<template>
  <div class="wrap">
    <h1>{{ error.statusCode }}</h1>
    <p>
      {{ error.statusMessage }}
    </p>
    <CommonBtn btn-color="primary" @click="navigateTo('/')">Voltar</CommonBtn>
  </div>
</template>

<script setup>
defineProps({
  error: {
    url: "",
    statusCode: 0,
    statusMessage: "",
    message: "",
    description: "",
    data: {},
  },
});
</script>

<style lang="scss" scoped>
.wrap {
    width: 100vw;
    height: 100vh;
    background-color: #0a0d14;
    color: $primary;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

}
</style>
