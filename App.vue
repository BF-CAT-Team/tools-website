<template>
  <div id="app" :class="theme">
    <a-layout>
      <a-layout-header>
        <div class="header-content">
          <h1>工具选择平台</h1>
          <a-switch v-model:checked="isDark" @change="toggleTheme" checked-children="🌙" un-checked-children="☀️" />
        </div>
      </a-layout-header>
      <a-layout-content style="padding: 20px;">
        <a-row>
          <a-col :span="6" class="tool-list">
            <ToolList @tool-selected="setCurrentTool" />
          </a-col>
          <a-col :span="18" class="tool-content">
            <component :is="currentTool === 'cookie' ? CookieForm : null" />
          </a-col>
        </a-row>
      </a-layout-content>
      <a-layout-footer>
        <a href="https://github.com/B1397KB/untitled">存储库链接</a> |
        <a href="https://bfvrobot.net">官网链接</a>
      </a-layout-footer>
    </a-layout>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import ToolList from './components/ToolList.vue';
import CookieForm from './components/CookieForm.vue';

const currentTool = ref('cookie');
const setCurrentTool = (tool) => {
  currentTool.value = tool;
};

const isDark = ref(false);
const theme = ref('light-theme');

const toggleTheme = () => {
  theme.value = isDark.value ? 'dark-theme' : 'light-theme';
};
</script>

<style scoped>
#app {
  transition: background-color 0.3s, color 0.3s;
}

.light-theme {
  background-color: #ffffff;
  color: #000000;
}

.dark-theme {
  background-color: #2c3e50;
  color: #ecf0f1;
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.tool-list {
  background-color: #f0f2f5;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.tool-content {
  border: 1px solid #d9d9d9;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

a-layout-header {
  background-color: #001529;
  color: #ffffff;
}

a-layout-footer {
  background-color: #f0f2f5;
  color: #000000;
  text-align: center;
}
</style>