<template>
  <q-card class="h-full flex flex-col">
    <!-- 头部 -->
    <div class="px-6 py-3 border-b">
      <div class=" flex items-center justify-between">
        <div class="my-text-secondary text-3xl font-semibold">设置</div>
        <q-btn flat round icon="close" @click="closeSettingsPanel" />
      </div>
    </div>

    <!-- 内容区域 -->
    <div class="flex-1 p-4 overflow-y-auto">
      <!-- 主题设置 -->
      <div class="mb-6">
        <div class="my-text-secondary text-xl font-semibold mb-4">
          主题设置
        </div>

        <div class="grid grid-cols-4 gap-3">
          <div v-for="theme in themeManager.themes" :key="theme.id" @click="selectTheme(theme.id)">
            <!-- 主题预览颜色 -->
            <div class="mb-2">
              <div class="flex h-12 rounded-lg overflow-hidden">
                <div class="flex-1" :style="{ backgroundColor: theme.previewColors[0] }" />
                <div class="flex-1" :style="{ backgroundColor: theme.previewColors[1] }" />
              </div>
            </div>

            <!-- 主题名称 -->
            <div class="flex-center my-text-secondary font-medium">
              {{ theme.label }}{{ themeManager.currentThemeId.value === theme.id ? ' (当前)' : '' }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </q-card>
</template>

<script setup lang="ts">
import { useSettingsStore } from '@core/stores';
import { useAppManagers } from '@core/stores';

const settingsStore = useSettingsStore();
const { themeManager } = useAppManagers();

// 关闭设置面板
const closeSettingsPanel = () => {
  settingsStore.closeSettingsPanel();
};

// 选择主题
const selectTheme = (themeId: string) => {
  themeManager.setTheme(themeId);
};
</script>

<style scoped lang="scss"></style>
