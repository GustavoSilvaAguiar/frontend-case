<template>
  <div class="wrap">
    <div
      class="comentario"
      v-for="(comentario, index) in comentarios"
      :key="index"
    >
      <img src="../../assets/images/avatar2.svg" />
      <div class="comentario--texto">
        <div class="comentario--texto--name">{{ comentario.nome }}</div>
        <div class="comentario--texto--msg">{{ comentario.msg }}</div>
      </div>
      <img
        v-if="comentario.like"
        src="../../assets/icons/Rating Items [1.0].svg"
      />
      <img
        v-if="!comentario.like"
        src="../../assets/icons/RatingItems2.svg"
      />
    </div>
  </div>
  <CommonBtn><template #icon>
    <img
        src="../../assets/icons/pencil-line.svg"
      />
  </template> Comment</CommonBtn>
</template>

<script lang="ts" setup>
const comentarios = [
  {
    nome: "James Brown",
    msg: "Parabéns, Matthew! 🔥",
    like: true,
  },
  {
    nome: "Lena Müller",
    msg: "Ótimo trabalho! 🤗",
    like: true,
  },
  {
    nome: "Juma Omondi",
    msg: "O céu é o limite! ⚡️",
    like: true,
  },
  {
    nome: "James Brown",
    msg: "Parabéns, Matthew! 🔥",
    like: false,
  },
  {
    nome: "Juma Omondi",
    msg: "O céu é o limite! ⚡️",
    like: false,
  },
  {
    nome: "Lena Müller",
    msg: "Ótimo trabalho! 🤗",
    like: true,
  },
  {
    nome: "Juma Omondi",
    msg: "O céu é o limite! ⚡️",
    like: false,
  },
  {
    nome: "Lena Müller",
    msg: "Ótimo trabalho! 🤗",
    like: true,
  },
];
</script>

<style lang="scss" scoped>
.wrap {
  max-height: 200px;
  overflow: auto;
}
.comentario {
  display: grid;
  align-items: center;
  grid-template-columns: auto 1fr auto;
  gap: 12px;

  img:nth-child(1) {
    width: 40px;
    height: 40px;
  }

  &--texto {
    display: flex;
    flex-direction: column;

    &--name {
      color: #525866;
      font-size: 12px;
      font-weight: 400;
    }
    &--msg {
      color: #0a0d14;
      font-size: 14px;
      font-weight: 400;
    }
  }
}
</style>
