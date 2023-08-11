<script setup>
import { onMounted } from 'vue'
import * as echarts from 'echarts'
import MainCard from '@/components/MainCard.vue'
const quickStartActions = ['表单配置', '托收费用…', '发票管理', '箱费用明…', '船舶使费…', '单箱信息…']
const dailyCapacity = [9000, 7000, 9000, 11451, 11321, 12256]
const dailyContainer = [900, 1000, 1145, 1000, 1250, 1135]

onMounted(() => {
    let workTrendChart = echarts.init(document.getElementById("chartWorkTrend"));
    workTrendChart.setOption({
        dataZoom: [
            {
                id: 'dataZoomX',
                type: 'slider',
                xAxisIndex: [0],
                filterMode: 'filter',
                show: true,
                start: 20,
                end: 80
            }
        ],
        legend: {
            data: ['业务1', '业务2', '业务3'],
            x: 'center',
            bottom: '50px',
            textStyle: {
                color: '#666'
            },
            icon: 'circle'
        },
        grid: {
            bottom: '100px',
            containLabel: true
        },
        tooltip: {
            trigger: 'axis',
            backgroundColor: '0px 10px 20px 0px rgba(167, 200, 255, 0.5),inset 0px -2px 12px 0px rgba(229, 237, 250, 0.5),inset 0px 2px 6px 0px rgba(229, 237, 250, 0.9)',
            backdropFilter: blur(),
            axisPointer: {
                type: 'cross',
                label: {
                    backgroundColor: '#6a7985'
                }
            }
        },
        xAxis: {
            type: 'category',
            boundaryGap: false,
            axisLine: {
                show: false
            },
            data: ['04:00', '05:00', '06:00', '07:00', '08:00', '09:00', '10:00', '11:00', '12:00', '13:00', '14:00']
        },
        yAxis: {
            type: 'value',
            axisLine: {
                show: false
            },
            axisLabel: {
                show: true,
                interval: 'auto',
                formatter: function (value) {
                    return value * 100 + '%';
                }
            }
        },
        grid: {
            bottom: '0px',
        },
        series: [{
            name: '业务1',
            data: [0.8, 0.9, 0.9, 0.5, 0.6, 0.5, 0.4, 0.3, 0.2, 0.3, 0.4, 0.6],
            type: 'line',
            smooth: true,
            symbol: 'none'
        },
        {
            name: '业务2',
            data: [0.7, 0.8, 0.8, 0.4, 0.5, 0.4, 0.3, 0.2, 0.1, 0.2, 0.3, 0.5],
            type: 'line',
            smooth: true,
            symbol: 'none'
        },
        {
            name: '业务3',
            data: [0.9, 1.0, 1.0, 0.6, 0.7, 0.6, 0.5, 0.4, 0.3, 0.4, 0.5, 0.7],
            type: 'line',
            smooth: true,
            symbol: 'none'
        },
        ],
        color: ['#0379FF', '#FEA501', '#13E1E1']
    })
    let dailyCapacityChart = echarts.init(document.getElementById("chartDailyCapacity"))
    dailyCapacityChart.setOption({
        xAxis: {
            type: 'category',
            boundaryGap: false,
            axisLine: {
                show: false
            },
            axisLabel: {
                show: false
            },
            axisTick: {
                show: false
            }
        },
        yAxis: {
            type: 'value',
            axisLine: {
                show: false
            },
            axisLabel: {
                show: false
            },
            splitLine: {
                show: false
            },
        },
        series: [{
            name: '业务1',
            data: dailyCapacity,
            type: 'line',
            smooth: true,
            symbol: 'none'
        }],
        color: ['#165dff']
    })
})
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
                    <!-- aaaa -->
                </template>
            </MainCard>
        </div>
        <MainCard title="数据概览" style="margin-top: 0.5rem;">
            <template #content>
                <div class="grid-cols-4">
                    <div class="rounded p2 mx"
                        style="height: 13vh; background: linear-gradient(180deg, #F2F9FE -3%, #E6F4FE 100%);">
                        <div class="w-full" style="font-size: small;">今日吞吐量（吨）</div>
                        <div class="w-full h-full relative">
                            <div class="absolute" style="left: 0; bottom: 14px; line-height: 25px;">
                                <div class="flex flex-row">
                                    <div>
                                        <p style="font-size: x-large;">{{ dailyCapacity[dailyCapacity.length - 1] }}</p>
                                        <p style="font-size: x-small; margin-left: 2px;">
                                            <span> 较昨日 </span>
                                            <span class="font-bold"
                                                :class="{ 'text-red': dailyCapacity[dailyCapacity.length - 1] > dailyCapacity[dailyCapacity.length - 2] },
                                                    { 'text-green': dailyCapacity[dailyCapacity.length - 1] < dailyCapacity[dailyCapacity.length - 2] }">{{
        ((dailyCapacity[dailyCapacity.length - 1] -
            dailyCapacity[dailyCapacity.length - 2]) /
            dailyCapacity[dailyCapacity.length - 2] * 100).toFixed(2) }}%</span>
                                        </p>
                                    </div>
                                    <div class="relative" style="width: 16px;">
                                        <img v-if="dailyCapacity[dailyCapacity.length - 1] >= dailyCapacity[dailyCapacity.length - 2]"
                                            src="@/assets/icons/uparrow.png" style="width: 12px; bottom: 7px; right: 0;"
                                            class="absolute object-contain" />
                                        <img v-else src="@/assets/icons/downarrow.png"
                                            style="width: 12px; bottom: 7px; right: 0;" class="absolute object-contain" />
                                    </div>
                                </div>
                            </div>
                            <div class="absolute" style="right: 0; top: 8px;">
                                <div id="chartDailyCapacity" style="height: 80px; width: 100px;">
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="rounded p2 mx" style="background: linear-gradient(180deg, #F5FEF2 -3%, #E6FEEE 100%);">
                        b</div>
                    <div class="rounded p2 mx" style="background: linear-gradient(180deg, #F2F9FE -3%, #E6F4FE 100%);">
                        c</div>
                    <div class="rounded p2 mx" style="background: linear-gradient(180deg, #F6F7FF -3%, #ECECFF 100%);">
                        d</div>
                </div>
            </template>
        </MainCard>
        <MainCard title="作业趋势分析" style="margin-top: 0.5rem;">
            <template #noMarginContent>
                <div id="chartWorkTrend" style="height: 49vh; width: 100%;"></div>
            </template>
        </MainCard>
    </div>
</template>

<style scoped>
.grid-cols-4 {
    display: grid;
    grid-template-columns: repeat(4, minmax(0, 1fr));
    /* gap: 0.5rem; */
}

.grid-cols-2 {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 0.5rem;
}
</style>
