<script setup>
import MainCard from '@/components/MainCard.vue'
const quickStartActions = ['表单配置', '托收费用…', '发票管理', '箱费用明…', '船舶使费…', '单箱信息…']
</script>

<template>
    <!-- background-color: #f5f7f9-->
    <div class="w-full p5" style="background-color: blue;">
        <div class="grid-cols-2 w-full">
            <MainCard title="快速开始">
                <template #content>
                    <div class="flex flex-row justify-between">
                        <div v-for="action in quickStartActions">
                            <img src="@/assets/icons/tempicon.png"
                                style="height: 4vh; margin-left: 0.5rem; margin-right: 0.5rem;" />
                            <div class=" text-center" style="font-size:x-small;">{{ action }}</div>
                        </div>
                    </div>
                </template>
            </MainCard>
            <MainCard title="系统消息">
                <template #content>

                </template>
            </MainCard>
        </div>
        <MainCard title="aaa" style="margin-top: 0.5rem;">
            <template #content>
                aaa
            </template>
        </MainCard>
    </div>
</template>

<style scoped>
.grid-cols-2 {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 0.5rem;
}
</style>
