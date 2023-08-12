<script setup>
import { SearchOutlined, TranslationOutlined, NotificationFilled } from '@vicons/antd'
</script>

<template>
    <div class="header justify-between flex flex-row sticky w-full bg-white ">
        <img src="@/assets/companylogo.png" />
        <div class="flex flex-row p1 h-full">
            <n-icon-wrapper class="header-icon" :size="24" :border-radius="9999" color="white" icon-color="black"
                style=" border-style: solid; border-color: darkgray; border-width: 1px;">
                <n-icon size="12">
                    <search-outlined />
                </n-icon>
            </n-icon-wrapper>
            <n-icon-wrapper class="header-icon" :size="24" :border-radius="9999" color="white" icon-color="black"
                style=" border-style: solid; border-color: darkgray; border-width: 1px;">
                <n-icon size="12">
                    <translation-outlined />
                </n-icon>
            </n-icon-wrapper>
            <n-icon-wrapper class="header-icon" :size="24" :border-radius="9999" color="white" icon-color="black"
                style=" border-style: solid; border-color: darkgray; border-width: 1px;">
                <n-icon size="12">
                    <notification-filled />
                </n-icon>
            </n-icon-wrapper>
            <div class="header-avatar bg-blue text-white font-bold text-center">A</div>
        </div>
    </div>
</template>

<style scoped>
.header {
    top: 0;
    right: 0;
    left: 0;
    z-index: 2001;
    box-shadow: 0 2px 4px 0 rgb(0, 0, 0, 10%);
    height: 6vh;
}

.header-icon {
    margin-top: 1vh;
    margin-right: 1rem;
}

.header-avatar {
    border-radius: 9999px;
    height: 4vh;
    width: 4vh;
    margin-top: 0.5vh;
    margin-right: 0.5rem;
}
</style>
