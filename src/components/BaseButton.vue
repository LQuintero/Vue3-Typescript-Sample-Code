<template>
  <button
    :disabled="disabled"
    :class="baseButtonStyle"
    @click="handleClick"
  >
    <slot />
  </button>
</template>

<script setup lang="ts">
import { computed } from 'vue'
// import ButtonType from "@/types"

const props = defineProps({
  selected: {
    type: Boolean,
    default: false
  },
  disabled: {
    type: Boolean,
    default: false
  },
  // type: {
  //   type: String as PropType<ButtonType>,
  //   default: ButtonType.button
  // }
})

const emit = defineEmits(['onClicked'])

function handleClick(event: MouseEvent) {
  emit('onClicked', event)
}

const baseButtonStyle = computed(() => {
  const selected = props.selected ? "selected" : "";
  return `base-button ${selected}`;
})

</script>

<style scoped>
.base-button {
  border-radius: 3px;
  font-size: 20px;
  font-weight: bold;
  cursor: pointer;
  border: none;
  padding: 5px;
  margin: 10px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-family: Lato;
  color: #284e6f;
}
.selected {
  color: white;
  background-color: #5587f8;
  border: 1px solid #5c778e;
  font-size: 20px;
}
:disabled {
  color: white;
  cursor: default;
}

</style>