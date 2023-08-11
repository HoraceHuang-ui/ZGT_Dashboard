<script setup>
</script>

<template>
    <div class="header justify-between flex flex-row sticky w-full">
        <img src="@/assets/companylogo.png" />
        <div class="flex flex-row p1 ">
            <img class="header-icon h-full" src="@/assets/icons/search.png" />
            <img class="header-icon h-full" src="@/assets/icons/translation.png" />
            <img class="header-icon h-full" src="@/assets/icons/notification.png" />
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
    height: 2vh;
    margin-top: 1.5vh;
    margin-right: 1rem;
}

.header-avatar {
    border-radius: 9999px;
    height: 4vh;
    width: 4vh;
    margin-top: 0.5vh;
}
</style>
