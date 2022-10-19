<script setup lang="ts">
import { ref } from 'vue'
import BaseButton from './components/BaseButton.vue'

let resultText = ref("No button(s) clicked")

function handleButton1Click(e: MouseEvent) {
  console.log("Button Clicked", e)
  resultText.value = "Button 1 Clicked"
}
function handleButton2lick(e: MouseEvent) {
  console.log("Button 2 Clicked", e)
  resultText.value = "Button 2 Clicked"
}
</script>

<template>
  <header>Sample Code</header>
  <main>
    <base-button
      @onClicked="handleButton1Click($event)"
    >
      Button 1
    </base-button>
    <base-button
      :selected="true"
      @onClicked="handleButton2lick($event)"
    >
      Button 2
    </base-button>
    <base-button
      :disabled="true"
    >
      Button 3
    </base-button>
    <label class="results">{{ resultText }}</label>
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

