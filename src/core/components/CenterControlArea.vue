<template>
  <div class="flex items-center gap-1 px-2">
    <div @click="handleSettings" class="w-8 h-7 flex-center" style="-webkit-app-region: no-drag" name="settings"
      title="设置">
      <i class="q-icon notranslate material-icons text-base">settings</i>
    </div>
    <button @click="handleMinimize"
      class="w-8 h-7 flex items-center justify-center text-slate-500 hover:text-slate-700 hover:bg-slate-200/70 rounded transition-all duration-200 hover:scale-105"
      style="-webkit-app-region: no-drag" title="最小化">
      <i class="q-icon notranslate material-icons text-base">minimize</i>
    </button>
    <button @click="handleMaximize"
      class="w-8 h-7 flex items-center justify-center text-slate-500 hover:text-slate-700 hover:bg-slate-200/70 rounded transition-all duration-200 hover:scale-105"
      style="-webkit-app-region: no-drag" :title="isMaximized ? '恢复' : '最大化'">
      <i class="q-icon notranslate material-icons text-base">{{ isMaximized ? 'filter_none' : 'crop_square' }}</i>
    </button>
    <button @click="handleClose"
      class="w-8 h-7 flex items-center justify-center text-slate-500 hover:text-white hover:bg-red-500 rounded transition-all duration-200 hover:scale-105"
      style="-webkit-app-region: no-drag" title="关闭">
      <i class="q-icon notranslate material-icons text-base">close</i>
    </button>
  </div>
</template>

<script setup lang="ts">
import { windowAPI } from '@core/api';
import { useSettingsStore } from '@core/stores';

const isMaximized = ref(false);
const settingsStore = useSettingsStore();

const handleSettings = () => {
  settingsStore.toggleSettingsPanel();
};

const handleMinimize = () => {
  windowAPI.minimize();
};

const handleMaximize = async () => {
  windowAPI.maximize();
  isMaximized.value = await windowAPI.isMaximized();
};

const handleClose = () => {
  windowAPI.close();
};

onMounted(async () => {
  isMaximized.value = await windowAPI.isMaximized();
});
</script>
