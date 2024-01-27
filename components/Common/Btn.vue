<template>
  <button :disabled="disabled" class="btnWrap" :class="switchBtnColor()">
    <slot name="icon"></slot>
    <slot></slot>
  </button>
</template>

<script lang="ts" setup>
const props = defineProps<{
  btnColor?: "primary" | "text";
  disabled?: boolean;
}>();

const switchBtnColor = () => {
  switch (props.btnColor) {
    case "primary":
      return "primary";

    case "text":
      return "text";

    default:
      break;
  }
};
</script>

<style lang="scss" scoped>
.btnWrap {
  cursor: pointer;
  display: flex;
  column-gap: 4px;
  align-items: center;
  font-size: 14px;
  font-weight: 500;
  padding: 10px;
  border-radius: 10px;
  background-color: #fff;
  box-shadow: 0px 1px 2px 0px rgba(82, 88, 102, 0.06);
  border: 1px solid #e2e4e9;
  justify-content: center;

  &:hover {
    scale: 1.01;
  }

  &:disabled {
    cursor: not-allowed;
    opacity: 0.5;
    scale: 1;
  }
}

.primary {
  background-color: $primary !important;
  color: $white;

  :deep .IconSVG {
    fill: $white;
  }
}
.text {
  background-color: transparent !important;
  color: $light-gray;
  border: none;

  :deep .IconSVG {
    fill: $white;
  }
}
</style>
