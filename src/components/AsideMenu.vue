<template>
  <n-menu :options="options" :collapsed="collapsed"/>
</template>

<script setup>
import {Accessible} from "@vicons/tabler"
import {LaptopOutlined,AppstoreOutlined,AlignRightOutlined,StockOutlined,FileTextOutlined,CheckCircleOutlined,ExclamationCircleOutlined,UserOutlined } from "@vicons/antd"
import {h} from "vue";
import {NIcon} from "naive-ui";


const options = [{
  label: '工作台',
  key: '1',
  icon: () => h(NIcon, null, {default: () => h(LaptopOutlined)}),
  children: [
  ]
}, {
  label: '预约管理',
  key: '2',
  icon: () => h(NIcon, null, {default: () => h(AppstoreOutlined)}),
  children: [
  ]
},{
  label: '闸口管理',
  key: '3',
  icon: () => h(NIcon, null, {default: () => h(AlignRightOutlined)}),
  children: [
  ]
}, {
  label: '堆场管理',
  key: '4',
  icon: () => h(NIcon, null, {default: () => h(StockOutlined)}),
  children: [
  ]
},{
  label: '箱务管理',
  key: '5',
  icon: () => h(NIcon, null, {default: () => h(FileTextOutlined)}),
  children: [
  ]
}, {
  label: '终端管理',
  key: '6',
  icon: () => h(NIcon, null, {default: () => h(CheckCircleOutlined)}),
  children: [
  ]
},{
  label: '车船管理',
  key: '7',
  icon: () => h(NIcon, null, {default: () => h(ExclamationCircleOutlined)}),
  children: [
  ]
}, {
  label: '查询统计',
  key: '8',
  icon: () => h(NIcon, null, {default: () => h(UserOutlined)}),
  children: [
  ]
},{
  label: '系统管理',
  key: '9',
  icon: () => h(NIcon, null, {default: () => h(UserOutlined)}),
  children: [
  ]
}]

</script>
