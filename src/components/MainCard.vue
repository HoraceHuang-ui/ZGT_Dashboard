<script setup>
const props = defineProps({
    title: String
})
</script>

<template>
    <div class="card relative">
        <div class="card-title absolute font-bold">{{ props.title }}</div>
        <slot name="noMarginContent"></slot>
        <div style="margin-top: 2.5rem;">
            <slot name="content"></slot>
        </div>
    </div>
</template>

<style scoped>
.card-title {
    top: 0.5rem;
    left: 0.75rem;
}

.card {
    border-radius: 0.25rem;
    background-color: white;
    padding: 0.5rem;
}
</style>
