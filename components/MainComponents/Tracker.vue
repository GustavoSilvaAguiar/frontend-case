<template>
  <div class="tracker">
    <div class="header">
      <div class="header--leftSide">
        <img src="../../assets/icons/timer-flash-line.svg" /> Rastreador de
        tempo
      </div>

      <CommonBtn
        ><template #icon
          ><img src="../../assets/icons/history-line.svg"
        /></template>
        Histórico</CommonBtn
      >
    </div>

    <div class="tracker--body">
      <div class="header tracker--body--header">
        <div class="header--leftSide">
          <img src="../../assets/icons/Monday.com.svg" />
          Track App
        </div>
        <img src="../../assets/icons/arrow-down-s-line.svg" />
      </div>
      <div class="tracker--body--main">
        <div>Aguardando</div>
        <div>
          {{ numerosFormatados.hora }} : {{ numerosFormatados.min }} :
          {{ numerosFormatados.segundo }}
        </div>
        <div @click="iniciarCronometro">btn</div>
        <div @click="pausarCronometro">pausar</div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
const horas = ref<number>(0);
const minutos = ref<number>(0);
const segundos = ref<number>(0);
const intervalID = ref();

const numerosFormatados = computed(() => {
  const segundo = formatarNumero(segundos.value);
  const min = formatarNumero(minutos.value);
  const hora = formatarNumero(horas.value);
  return { segundo, min, hora };
});

const formatarNumero = (valor: number) => {
  return valor.toLocaleString("en-US", {
    minimumIntegerDigits: 2,
    useGrouping: false,
  });
};

const iniciarCronometro = () => {
  intervalID.value = setInterval(() => {
    segundos.value++;
    if (segundos.value === 60) {
      segundos.value = 0;
      minutos.value++;
    }

    if (minutos.value === 60) {
      minutos.value = 0;
      horas.value++;
    }
  }, 1000);
};

const pausarCronometro = () => {
  clearInterval(intervalID.value);
};

const resetarCronometro = () => {
  minutos.value = 0;
  segundos.value = 0;
  horas.value = 0;
};
</script>

<style lang="scss" scoped>
.tracker {
  display: flex;
  flex-direction: column;
  row-gap: 16px;
  border-radius: 16px;
  padding: 16px;
  border: 1px solid #e2e4e9;
  box-shadow: 0px 1px 2px 0px rgba(228, 229, 231, 0.24);
  width: calc(100% - 32px);
  height: calc(100% - 32px);

  &--body {
    border-radius: 10px;
    border: 1px solid #e2e4e9;
    box-shadow: 0px 1px 2px 0px rgba(228, 229, 231, 0.24);

    &--header {
      border-radius: 10px 10px 0px 0px;
      border-bottom: 1px solid #e2e4e9;
      background: #f6f8fa;
      padding: 10px;
    }

    &--main {
      padding: 16px;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
  }
}
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  column-gap: 8px;

  &--leftSide {
    display: flex;
    align-items: center;
    gap: 8px;
  }
}
</style>
