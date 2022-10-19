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
import { defineComponent, computed } from 'vue'

export default defineComponent({
  props: {
    variant: {
      type: String,
      default: null
    },
    selected: {
      type: Boolean,
      default: false
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },
  setup(props) {
    const baseButtonStyle = computed(() => {
    const selected = props.selected ? "selected" : "";
    return `base-button ${selected}`;
    })

    return { baseButtonStyle }
  },
  methods: {
    handleClick(event: MouseEvent) {
      this.$emit('onClicked', event)
    },
    hoverCallback(isHovering: Boolean) {
      this.$emit('onHover', isHovering)
    }
  }
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
:hover {
  opacity: 0.8;
}
:disabled {
  color: white;
  cursor: default;
  pointer-events: none;
}
.selected {
  color: white;
  background-color: #5587f8;
  border: 1px solid #5c778e;
  font-size: 20px;
}
</style>