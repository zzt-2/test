<template>
  <div class="flex items-center justify-between border-b border-gray-200" style="-webkit-app-region: drag">
    <!-- 左侧标题区域 -->
    <div class="flex items-center p-1">
      Title
    </div>
    <!-- 中间控制区域 -->
    <CenterControlArea />

    <!-- 右侧窗口控制按钮 -->
    <div class="flex items-center gap-1">
      <button @click="handleMinimize"
        class="w-8 h-7 flex items-center justify-center text-slate-500 hover:text-slate-700 hover:bg-slate-200/70 rounded transition-all duration-200 hover:scale-105"
        style="-webkit-app-region: no-drag" title="最小化">
        <i class="q-icon notranslate material-icons text-base">minimize</i>
      </button>
      <button @click="handleMaximize"
        class="w-8 h-7 flex items-center justify-center text-slate-500 hover:text-slate-700 hover:bg-slate-200/70 rounded transition-all duration-200 hover:scale-105"
        style="-webkit-app-region: no-drag" title="最大化">
        <i class="q-icon notranslate material-icons text-base">crop_square</i>
      </button>
      <button @click="handleClose"
        class="w-8 h-7 flex items-center justify-center text-slate-500 hover:text-white hover:bg-red-500 rounded transition-all duration-200 hover:scale-105"
        style="-webkit-app-region: no-drag" title="关闭">
        <i class="q-icon notranslate material-icons text-base">close</i>
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { windowAPI } from '@core/api';



const handleMinimize = () => {
  windowAPI.minimize();
};

const handleMaximize = () => {
  windowAPI.maximize();
};

const handleClose = () => {
  windowAPI.close();
};
</script>
