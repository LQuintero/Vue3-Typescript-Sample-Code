<script setup lang="ts">
import { ref } from 'vue'
import BaseButton from './components/BaseButton.vue'

const resultLabel = ref("No button(s) clicked")
let resultAText = 'Button A Clicked 0 times';
let resultBText = 'Button B Clicked 0 times';
let buttonAClickCount = 0;
let buttonBClickCount = 0;

function handleButton1Click() {
  buttonAClickCount++;
  resultAText = `Button A Clicked ${buttonAClickCount} times`
  resultLabel.value = resultAText;
}
function handleButtonBClick() {
  buttonBClickCount++;
  resultBText = `Button B Clicked ${buttonBClickCount} times`
  resultLabel.value = resultBText
}
function handleButtonHover(e: MouseEvent, isHovering: Boolean) {
  if ((e.target as Element).className. includes('selected')) {
    resultLabel.value = isHovering ? "Button B is hovered" : resultBText
  } else {
    resultLabel.value = isHovering ? "Button A is hovered" : resultAText
  }
}
</script>

<template>
  <header>Sample Code</header>
  <main>
    <base-button
      @onClicked="handleButton1Click"
      @mouseover="handleButtonHover($event, true)"
      @mouseleave="handleButtonHover($event, false)"
    >
    Button A
    </base-button>
    <base-button
      :selected="true"
      @onClicked="handleButtonBClick($event)"
      @mouseover="handleButtonHover($event, true)"
      @mouseleave="handleButtonHover($event, false)"
    >
    Button B
    </base-button>
    <base-button
      :disabled="true"
    >
    Button C
    </base-button>
    <label class="results">{{ resultLabel }}</label>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
  padding: 10px;
  color: white;
  font-size: 30px;
}
main {
  margin: 12px;
}
.results {
  margin-left: 20px;
  padding: 10px;
}
</style>

