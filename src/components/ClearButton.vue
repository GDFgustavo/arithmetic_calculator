<script setup>
const props = defineProps(['limpaValores'])
</script>

<template>
    <div class="row">
        <div class="col mt-4">
            <button @click="props.limpaValores" type="button" class="btn border-white button-clear">C</button>
        </div>
    </div>
</template>

<style scoped>
.button-clear {
    color: #fff;
}

.button-clear:hover {
    background-color: #fff;
    color: #000;
}
</style>