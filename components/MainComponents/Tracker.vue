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
        <div class="tracker--body--main--text">Aguardando</div>
        <div class="tracker--body--main--timer">
          {{ numerosFormatados.hora }}:{{ numerosFormatados.min }}:{{
            numerosFormatados.segundo
          }}
        </div>
        <div class="tracker--body--main--functions">
          <div
            v-if="showBtn() === 'start' || showBtn() === 'pause'"
            class="tracker--body--main--functions--btn"
            @click="iniciarCronometro"
          >
            <img src="../../assets/icons/play-fill.svg" /> Iniciar
          </div>
          <div
            v-if="showBtn() === 'counting'"
            class="tracker--body--main--functions--btn"
            @click="pausarCronometro"
          >
            <img src="../../assets/icons/pause-circle-fill.svg" />Pausar
          </div>
          <span
            v-if="showBtn() === 'counting' || showBtn() === 'pause'"
            class="divider"
          />
          <div
            v-if="showBtn() === 'counting' || showBtn() === 'pause'"
            class="tracker--body--main--functions--btn"
            @click="resetarCronometro"
          >
            <img src="../../assets/icons/stop-circle-fill.svg" />Parar
          </div>
        </div>
      </div>
    </div>

    <div class="tracker--bottom">
      TAREFAS ANTERIORES
      <TrackerComponentsRecords time="1:23:05">
        <template #logo><img src="../../assets/icons/loom.svg" /></template>
        Alinhamento - Comercial</TrackerComponentsRecords
      >
      <TrackerComponentsRecords time="3:14:26">
        <template #logo><img src="../../assets/icons/Evernote.svg" /></template>
        Evernote App Redesign</TrackerComponentsRecords
      >
    </div>
  </div>
</template>

<script lang="ts" setup>
const horas = ref<number>(0);
const minutos = ref<number>(0);
const segundos = ref<number>(0);
const intervalID = ref();
const counting = ref<boolean>(false);

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
  counting.value = true;
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
  counting.value = false;
};

const resetarCronometro = () => {
  pausarCronometro();
  minutos.value = 0;
  segundos.value = 0;
  horas.value = 0;
  counting.value = false;
};

const showBtn = () => {
  if (
    horas.value == 0 &&
    minutos.value === 0 &&
    segundos.value === 0 &&
    !counting.value
  ) {
    return "start";
  } else if (counting.value) {
    return "counting";
  } else if (
    (horas.value !== 0 || minutos.value !== 0 || segundos.value !== 0) &&
    !counting.value
  ) {
    return "pause";
  }
};
</script>

<style lang="scss" scoped>
.divider {
  width: 1px;
  height: 12px;
  background-color: #cdd0d5;
}
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

      &--text {
        color: #868c98;
        font-size: 11px;
        font-weight: 500;
        text-transform: uppercase;
      }

      &--timer {
        color: #0a0d14;
        font-size: 40px;
        font-weight: 500;
      }

      &--functions {
        display: flex;
        align-items: center;
        column-gap: 16px;

        &--btn {
          display: flex;
          align-items: center;
          column-gap: 4px;
        }
      }
    }
  }

  &--bottom {
    display: flex;
    flex-direction: column;
    row-gap: 14px;
    color: #868c98;
    font-size: 11px;
    font-weight: 500;

    //&--records {
    //  display: grid;
    //  grid-template-columns: auto 1fr auto;
    //  gap: 10px;
    //  align-items: center;
    //
    //  &--title {
    //    font-size: 14px;
    //    font-weight: 400;
    //    color: #0a0d14;
    //  }
    //  .logo {
    //    border-radius: 48px;
    //    border: 1px solid #e2e4e9;
    //    padding: 8px;
    //  }
    //}
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
