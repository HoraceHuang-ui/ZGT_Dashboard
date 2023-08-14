<script setup>
import { onMounted, ref } from 'vue'
import DataOverviewCard from '@/components/DataOverviewCard.vue'
import * as echarts from 'echarts'
import MainCard from '@/components/MainCard.vue'

const quickStartActions = ['表单配置', '托收费用明细', '发票管理', '箱费用明细', '船舶使明细', '单箱信息详情']
const dailyCapacity = [9000, 7000, 9000, 8765, 9680, 11451, 11321, 12256]
const dailyContainer = [900, 1000, 1145, 1012, 1098, 1299, 999, 1250, 1145]
const annualCapacity = [300000, 400009, 299901, 451042, 432101, 398071, 489095, 514114]
const annualContainer = [9000, 10112, 9876, 8654, 10230, 11234, 11451, 10119]
const notifications = ref([{
    title: '测试标题测试标题测试标题测试标题测试标题',
    msg: '测试正文测试正文测试正文测试正文测试正文测试正文测试正文测试正文测试正文测试正文测试正文',
    timestamp: Date.now(),
    urgent: true
}, {
    title: '测试标题2',
    msg: '测试正文2',
    timestamp: Date.now(),
    urgent: false
}])

onMounted(() => {
    console.log(notifications.value.length)
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
})
</script>

<template>
    <!-- background-color: #f5f7f9-->
    <div class="w-full p5" style="background-color: blue;">
        <div class="grid-cols-2 w-full">
            <MainCard title="快速开始">
                <template #content>
                    <div class="flex flex-row justify-between">
                        <div v-for="action in quickStartActions" style="max-width: 15%; justify-content: center;">
                            <img class="w-full object-contain" src="@/assets/icons/tempicon.png" style="height: 4vh;" />
                            <n-ellipsis class="w-full text-center" style="font-size:x-small;">{{ action }}</n-ellipsis>
                        </div>
                    </div>
                </template>
            </MainCard>
            <MainCard title="系统消息">
                <template #content>
                    <n-scrollbar v-if="notifications && notifications.length > 0"
                        class="justify-center justify-items-center px w-full" style="max-height: 10vh;" trigger="none">
                        <div v-for="ntf in notifications" style="width: 86%;">
                            <div class="flex flex-row justify-between w-full">
                                <div class="w-full">
                                    <p>
                                        <n-ellipsis class=" text-blue" style="max-width: 50%;">{{ ntf.title }}</n-ellipsis>
                                        <span class="text-gray" style="font-size: smaller; margin-left: 4px;">{{
                                            new Date(ntf.timestamp).toLocaleString() }}</span>
                                    </p>
                                    <n-ellipsis class="w-full" style=" max-height: 1lh;">
                                        <span>{{ ntf.msg }}</span>
                                    </n-ellipsis>
                                </div>
                                <div style="min-width: 1px;">
                                    <n-tag v-if="ntf.urgent" round type="error">紧急</n-tag>
                                </div>
                            </div>
                            <div style="height: 0.5rem;" />
                        </div>
                    </n-scrollbar>
                    <div class="w-full text-center" v-else>暂无消息</div>
                </template>
            </MainCard>
        </div>
        <MainCard title="数据概览" style="margin-top: 0.5rem;">
            <template #content>
                <div class="grid-cols-4">
                    <DataOverviewCard title="今日吞吐量(吨)" :dataArr="dailyCapacity" linePlot comparisonStr="较昨日"
                        style="height: 13vh; background: linear-gradient(180deg, #F2F9FE -3%, #E6F4FE 100%);" />
                    <DataOverviewCard title="今日集装箱(个)" :dataArr="dailyContainer" comparisonStr="较昨日"
                        style="height: 13vh; background: linear-gradient(180deg, #F5FEF2 -3%, #E6FEEE 100%);" />
                    <DataOverviewCard title="今年总吞吐量(吨)" :dataArr="annualCapacity" linePlot comparison-str="较去年"
                        style="height: 13vh; background: linear-gradient(180deg, #F2F9FE -3%, #E6F4FE 100%);" />
                    <DataOverviewCard title="今年总集装箱(个)" :dataArr="annualContainer" comparison-str="较去年"
                        style="height: 13vh; background: linear-gradient(180deg, #F6F7FF -3%, #ECECFF 100%);" />
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
