<template>
  <n-switch v-model:value="collapsed"/>
  <n-menu :options="options" :collapsed="collapsed"/>
</template>

<script setup>
import {Accessible} from "@vicons/tabler"
import {h, ref} from "vue";
import {NIcon} from "naive-ui";

const collapsed = ref(false)

const options = [{
  label: '射手',
  key: 'adc',
  icon: () => h(NIcon, null, {default: () => h(Accessible)}),
  children: [
    {
      label: "ez",
      key: "ez",
      icon: () => h(NIcon, null, {default: () => h(Accessible)}),
    }, {
      label: "mf",
      key: "mf",
      icon: () => h(NIcon, null, {default: () => h(Accessible)}),
    }
  ]
}, {
  label: '射手1',
  key: 'adc1',
  icon: () => h(NIcon, null, {default: () => h(Accessible)}),
  children: [
    {
      label: "ez1",
      key: "ez1",
      icon: () => h(NIcon, null, {default: () => h(Accessible)}),
    }, {
      label: "mf1",
      key: "mf1",
      icon: () => h(NIcon, null, {default: () => h(Accessible)}),
    }
  ]
}]

</script>
