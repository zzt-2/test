<template>
  <div class="w-full h-3rem flex items-center justify-between z-1" style="-webkit-app-region: drag">
    <!-- 标题区域 -->
    <div class="absolute w-full flex items-center justify-center text-2xl p-1 font-orbitron tracking-[0.4rem]">
      Title标题
      <div
        class="absolute -bottom-1 left-30% right-30% h-0.2rem bg-gradient-to-r from-transparent via-[var(--text-primary)] to-transparent" />
    </div>

    <!-- 按钮组 -->
    <div class="flex items-center gap-1 px-2">
      <button @click="handleMinimize"
        class="w-8 h-7 flex items-center justify-center text-slate-500 hover:text-slate-700 hover:bg-slate-200/70 rounded transition-all duration-200 hover:scale-105"
        style="-webkit-app-region: no-drag" title="最小化">
        <i class="q-icon notranslate material-icons text-base">minimize</i>
      </button>
    </div>

    <!-- 控制区域 -->
    <CenterControlArea />
  </div>
</template>

<script setup lang="ts">
</script>
