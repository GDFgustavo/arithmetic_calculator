<script setup>
const props = defineProps(['op'])
</script>

<template>
    <div class="row">
        <div class="col-md-12">
            <select @change="props.op" class="form-control">
                <option value="+">Somar</option>
                <option value="-">Diminuir</option>
                <option value="*">Multiplicar</option>
                <option value="/">Dividir</option>
                <option value="%">Porcentagem</option>
            </select>
        </div>
    </div>
</template>