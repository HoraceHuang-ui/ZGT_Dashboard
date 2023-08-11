<script setup>
</script>

<template>
    <!-- background-color: #f5f7f9-->
    <div class="flex w-full h-full p3" style="background-color: #f5f7f9;">
        <div class="grid-cols-2 w-full p2">
            <div class="card">
                <div class="" style="margin-top: 2rem;">aaa</div>
            </div>
            <div class="card">bbb</div>
        </div>
    </div>
</template>

<style scoped>
.card {
    position: relative;
    border-radius: 0.25rem;
    background-color: white;
    padding: 0.5rem;
}

.grid-cols-2 {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 0.5rem;
}
</style>
