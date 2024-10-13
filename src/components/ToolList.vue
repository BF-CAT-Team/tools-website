<template>
  <a-menu @click="handleClick" mode="vertical" class="tool-menu">
    <a-menu-item key="cookie">Cookie 获取工具</a-menu-item>
  </a-menu>
</template>

<script setup>
const handleClick = (e) => {
  emit('tool-selected', e.key);
};
</script>

<style scoped>
.tool-menu {
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}
</style>