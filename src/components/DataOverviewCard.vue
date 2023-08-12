<script setup>
import { onMounted, ref } from 'vue';
import * as echarts from 'echarts'

const props = defineProps({
    title: String,
    dataArr: [],
    linePlot: {
        type: Boolean,
        default: false
    }
})

const echartref = ref()

const len = props.dataArr.length
onMounted(() => {
    let lineOptions = {
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
            min: findMin(props.dataArr) * 0.6,
            max: findMax(props.dataArr) * 1.3,
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
            data: props.dataArr,
            type: 'line',
            smooth: true,
            symbol: 'none'
        }],
        color: ['#165dff']
    }
    let boxOptions = {
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
            min: findMin(props.dataArr) * 0.6,
            max: findMax(props.dataArr) * 1.3,
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
            data: props.dataArr,
            type: 'bar',
            symbol: 'none',
            itemStyle: {
                normal: {
                    barBorderRadius: [5, 5, 0, 0]
                }
            }
        }],
        color: ['#4fba60']
    }
    let myChart = echarts.init(echartref.value);
    // let myChart = echarts.init(echartref)
    myChart.setOption(props.linePlot ? lineOptions : boxOptions)
})

const findMin = () => {
    var min = 999999
    props.dataArr.forEach(num => {
        if (num < min) {
            min = num
        }
    })
    return min
}
const findMax = () => {
    var max = -1
    props.dataArr.forEach(num => {
        if (num > max) {
            max = num
        }
    })
    return max
}
</script>
<template>
    <div class="rounded p2 mx">
        <div class="w-full" style="font-size: small;">{{ props.title }}</div>
        <div class="w-full h-full relative">
            <div class="absolute" style="left: 0; bottom: 14px; line-height: 25px;">
                <div class="flex flex-row">
                    <div>
                        <p style="font-size: x-large;">{{ props.dataArr[len - 1] }}</p>
                        <p style="font-size: x-small; margin-left: 2px;">
                            <span> 较昨日 </span>
                            <span class="font-bold" :class="{ 'text-red': props.dataArr[len - 1] > props.dataArr[len - 2] },
                                { 'text-green': props.dataArr[len - 1] < props.dataArr[len - 2] }">{{
        ((props.dataArr[len - 1] -
            props.dataArr[len - 2]) /
            props.dataArr[len - 2] * 100).toFixed(2) }}%</span>
                        </p>
                    </div>
                    <div class="relative" style="width: 16px;">
                        <img v-if="props.dataArr[len - 1] >= props.dataArr[len - 2]" src="@/assets/icons/uparrow.png"
                            style="width: 12px; bottom: 7px; right: 0;" class="absolute object-contain" />
                        <img v-else src="@/assets/icons/downarrow.png" style="width: 12px; bottom: 7px; right: 0;"
                            class="absolute object-contain" />
                    </div>
                </div>
            </div>
            <div class="absolute" style="right: 0; top: 8px;">
                <div ref="echartref" style="height: 50px; width: 100px;">
                </div>
            </div>
        </div>
    </div>
</template>
