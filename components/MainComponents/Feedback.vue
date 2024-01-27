<template>
  <div class="feedback">
    <div class="feedback--header text">
      <img src="../../assets/icons/discuss-line.svg" /> Feedback diário
    </div>
    <div class="divider" />
    <div class="feedback--main">
      <img src="../../assets/icons/user-smile-line.svg" />
      <div class="feedback--main--text">
        <div class="text">Como você classificaria seu humor hoje?</div>
        <div>Compartilhe seu humor para nos ajudar a entender.</div>
      </div>
    </div>
    <div class="addComentario">
      <div class="addComentario--btn">
        <div @click="addEmoji('😔')">😔</div>
        <div @click="addEmoji('😕')">😕</div>
        <div @click="addEmoji('😐')">😐</div>
        <div @click="addEmoji('🙂')">🙂</div>
        <div @click="addEmoji('😄')">😄</div>
      </div>
      <textarea v-model="text"></textarea>
    </div>
    <CommonBtn @click="enviar">Enviar</CommonBtn>
  </div>
</template>

<script lang="ts" setup>
const text = ref<string>("");

const addEmoji = (emoji: string) => {
  text.value = text.value + emoji;
};

const enviar = () => {
  text.value = "";
};
</script>

<style lang="scss" scoped>
.addComentario {
  height: 120px;

  &--btn {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    div {
      text-align: center;
      width: 100%;
      border: 1px solid var(--stroke-soft-200, #e2e4e9);
      background: var(--bg-white-0, #fff);
      padding: 8px 4px;
      cursor: pointer;
    }

    div:nth-child(1) {
      border-radius: 12px 0px 0px 0px;
    }
    div:nth-child(5) {
      border-radius: 0px 12px 0px 0px;
    }
  }
}
textarea {
  margin: 0;
  padding: 0;
  resize: none;
  border: 1px solid #e2e4e9;
  box-shadow: 0px 1px 2px 0px rgba(228, 229, 231, 0.24);
  border-radius: 0px 0px 12px 12px;
  width: calc(100% - 1.334px);
  height: calc(100% - 40px);
}
.feedback {
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
    display: flex;
    align-items: center;
    gap: 8px;
  }

  &--main {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 12px;

    img {
      padding: 8px;
      border-radius: 56px;
      background: #fef3eb;
      width: 40px;
      height: 40px;
    }

    &--text {
      color: #525866;
      text-align: center;
      font-size: 12px;
      font-weight: 400;
    }
  }
}
.text {
  color: #0a0d14;
  font-size: 16px;
  font-weight: 500;
}
.divider {
  height: 1px;
  background: #e2e4e9;
}
</style>
