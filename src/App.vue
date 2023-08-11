<script setup lang="ts">
import { RouterView } from 'vue-router'
import TopHeader from '@/components/TopHeader.vue'
</script>

<template>
  <TopHeader></TopHeader>
  <n-layout has-sider>
    <n-layout-sider bordered width="15vw" collapse-mode="width" :collapsed-width="64" show-trigger>
      <n-menu>

      </n-menu>
    </n-layout-sider>
    <n-layout-content>
      <RouterView />
    </n-layout-content>
  </n-layout>
</template>

<style scoped>
</style>
