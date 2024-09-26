<script setup>
import { reactive } from 'vue';

  import Display from './components/Display.vue';
  import InputField from './components/InputField.vue';
  import OperationSelect from './components/OperationSelect.vue';
  import ClearButton from './components/ClearButton.vue';

const estado = reactive({
  value1: '',
  value2: '',
  op: '+',
  error: '',
})

const limpaValores = () => {
  estado.value1 = ''
  estado.value2 = ''
}

const calcular = () => {
  const { op } = estado

  try {
    const num1 = Number(estado.value1) // Convertendo para o tipo number
    const num2 = Number(estado.value2)

    switch (op) {
    case '+':
      return num1 + num2;
    case '-':
      return num1 - num2;
    case '*':
      return num1 * num2;
    case '/':
      return num1 / num2;
    case '%':
      return num1 % num2;
  }
  }catch {
    estado.error = 'Formato Inválido';
  }
}

</script>

<template>
  <div class="container">
    <div class="calculator rounded-4 p-5">

      <Display
      :calcular="calcular()"
      :error="estado.error">
      </Display>

      <InputField 
      :value1="estado.value1"
      :att-value1="evento => estado.value1 = evento.target.value"
      :value2="estado.value2" 
      :att-value2="evento => estado.value2 = evento.target.value"
      :op="estado.op">
      </InputField>

      <OperationSelect 
      :op="evento => estado.op = evento.target.value">
      </OperationSelect>

      <ClearButton
      :limpa-valores="limpaValores">
      </ClearButton>


    </div>
  </div>
</template>

<!-- Style global -->
<style> 
#app {
  background-color: rgb(36, 36, 36);
}
</style>

<!-- Style dos componentes -->
<style scoped>
.container {
  max-width: 100%;
  width: 500px;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* .calculator {
  border: 1px solid #ffffff;
  box-shadow: rgba(0, 0, 0, 0.19) 0px 10px 20px, rgba(0, 0, 0, 0.23) 0px 6px 6px;
} */
</style>
