<script setup>
import MainCard from '@/components/MainCard.vue'
const quickStarActions = ['表单配置', '托收费用…', '发票管理', '箱费用明…', '船舶使费…', '单箱信息…']
</script>

<template>
    <!-- background-color: #f5f7f9-->
    <div class="flex w-full h-full p3" style="background-color: blue;">
        <div class="grid-cols-2 w-full p2">
            <MainCard title="快速开始">
                <template #content>
                    <div class="flex flex-row justify-between">
                        <div v-for="action in quickStarActions">
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
    </div>
</template>

<style scoped>
.grid-cols-2 {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 0.5rem;
}
</style>
