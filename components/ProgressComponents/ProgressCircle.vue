<template>
  <div class="box-circle">
    <svg>
      <circle cx="40" cy="40" r="40"></circle>
      <circle id="cirleProgress" cx="40" cy="40" r="40"></circle>
    </svg>
    <div class="number">{{ props.porcentagem }}%</div>
  </div>
</template>

<script lang="ts" setup>
const props = defineProps({
  porcentagem: {
    type: Number,
    default: 0,
  },
});
const circle = ref<HTMLElement | null>(null);

onMounted(() => {
  circle.value = document.getElementById("cirleProgress") as HTMLElement;
  circle.value.style.strokeDashoffset = `${252 - (252 * props.porcentagem) / 100}`;
  calcCircle;
});


const calcCircle = () => {
  if (circle.value) {
    circle.value.style.strokeDashoffset = `${252 - (252 * props.porcentagem) / 100}`;
  }
};
</script>

<style lang="scss" scoped>
.box-circle {
  position: relative;
  width: 90px;
  height: 90px;
}

circle {
  height: 80px;
  width: 80px;
  fill: none;
  stroke: $primary;
  stroke-width: 7px;
  transform: translate(4px, 4px);
  stroke-dasharray: 252;
  stroke-dashoffset: 252;
}

circle:nth-child(1) {
  stroke-dashoffset: 0;
  stroke: #e2e4e9;
}
svg {
  height: 88px;
  width: 88px;
}
circle:nth-child(2) {
  transform-origin: center center;
  rotate: -90deg;
  transition: all 1s;
  stroke: $primary;
}
.number {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 17px;
  font-weight: 900;
  color: #0a0d14;
}
</style>
