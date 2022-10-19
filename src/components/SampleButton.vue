<script setup lang="ts">
//setup scope
import { computed, defineEmits } from 'vue'

const props = defineProps({
  selected: {
    type: Boolean,
    default: false
  },
  disabled: {
    type: Boolean,
    default: false
  }
})

const emit = defineEmits<{
  (event: 'onClicked', e: MouseEvent): void,
  (event: 'onHover', isHovering: Boolean): void
}>()
function handleClick(event: MouseEvent) {
  emit('onClicked', event)
}
function hoverCallback(isHovering: Boolean) {
  emit('onHover', isHovering)
}

const baseButtonStyle = computed(() => {
  const selected = props.selected ? "selected" : "";
  return `base-button ${selected}`;
})

</script>

<template>
  <button
    :disabled="disabled"
    :class="baseButtonStyle"
    @click="handleClick"
    @mouseover="hoverCallback(true)"
    @mouseleave="hoverCallback(false)"
  >
    <slot />
  </button>
</template>

<script lang="ts">
// module scope
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