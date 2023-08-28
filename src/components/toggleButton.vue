<template>
  <div class="container">
    <div
      class="toggle-button"
      @click="enableOrDisableDarkMode"
    >
      Enable
    </div>
  </div>
</template>

<script lang="ts" setup>
async function enableOrDisableDarkMode() {
  const [tab] = await chrome.tabs.query({
    active: true,
    lastFocusedWindow: true,
  });
  chrome.scripting.executeScript({
    target: { tabId: tab.id },
    files: ["content.js"],
  });
}
</script>

<style scoped>
.container {
  width: 400px;
  height: 100px;
  background-color: rgb(45, 44, 44);
}
.toggle-button {
  height: 50px;
  width: 200px;
  border-radius: 10px;
  margin: auto;
  border: 1px solid lightgrey;
  font-size: 2rem;
  font-weight: 500;
  cursor: pointer;
  background-color: rgb(69, 68, 68);
  color: white;
}
.container,
.toggle-button {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>