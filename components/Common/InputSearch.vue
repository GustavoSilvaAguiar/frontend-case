<template>
  <div class="inputWrap">
    <img src="../../assets/icons/search-2-line.svg" />
    <input v-model="text" @keyup="$emit('search', text)" type="text" placeholder="Pesquisar cursos..." />
  </div>
</template>

<script lang="ts" setup>
const text = ref<string>()
</script>

<style lang="scss" scoped>
.inputWrap {
  display: flex;
  align-items: center;
  column-gap: 8px;
  border-radius: 8px;
  padding: 8px;
  border: 1px solid #e2e4e9;
  box-shadow: 0px 1px 2px 0px rgba(228, 229, 231, 0.24);

  img {
    cursor: pointer;
  }

  input {
    width: 100%;
    border: none;
  }
}
</style>
