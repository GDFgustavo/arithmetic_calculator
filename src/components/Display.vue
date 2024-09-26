<script setup>
const props = defineProps(['calcular', 'error'])
</script>
<template>
    <div class="calculator-display text-break text-end mb-5">
        <h1 class="text-white fw-normal">{{ props.calcular }}|</h1>
    </div>
    <div class="">
        <h2 class="text-white m-2 d-flex justify-content-center">{{ props.error }}</h2>
    </div>
</template>

<style scoped>
.calculator-display {
    height: 90px;
    overflow-y: scroll;
    border-bottom: 1px solid #3f3f3f;
}

::-webkit-scrollbar {
    width: 0px;
}
</style>