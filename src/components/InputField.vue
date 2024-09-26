<script setup>
const props = defineProps(['value1', 'attValue1', 'value2', 'attValue2', 'op'])
</script>

<template>
    <form>
        <div class="row calculator-value mb-4">
            <div class="col">
                <input id="input-1" :value="props.value1" @input="props.attValue1" class="form-control focus-ring focus-ring-dark border-0"
                    type="number" placeholder="000">
                <label class="text-white text-uppercase fw-semibold d-flex justify-content-center"
                    for="input-1">Valor-1</label>
            </div>
            <div class="col-1 text-white fs-3 text-center op">{{ props.op }}</div>
            <div class="col">
                <input id="input-2" :value="props.value2" @input="props.attValue2" class="form-control focus-ring focus-ring-dark border-0"
                    type="number" placeholder="000">
                <label class="text-white text-uppercase fw-semibold d-flex justify-content-center"
                    for="input-2">Valor-2</label>
            </div>
        </div>
    </form>
</template>