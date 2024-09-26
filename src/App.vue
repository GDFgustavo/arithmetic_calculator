<script setup>
import { reactive } from 'vue';

const estado = reactive({
  value1: '',
  value2: '',
  op: '+',
  error: '',
  eVisivel: false,
})

const limpaValores = () => {
  estado.value1 = ''
  estado.value2 = ''
}

const calcular = () => {
  const { op } = estado

  try {
    switch (op) {
    case '+':
      return estado.value1 + estado.value2;
    case '-':
      return estado.value1 - estado.value2;
    case '*':
      return estado.value1 * estado.value2;
    case '/':
      return estado.value1 / estado.value2;
    case '%':
      return estado.value1 % estado.value2;
  }
  }catch {
    estado.error = 'Formato Inválido';
  }
}

</script>

<template>
  <div class="container">
    <div class="calculator rounded-4 p-5">
      <div class="calculator-display text-break text-end mb-5">
        <h1 class="text-white fw-normal">{{ calcular() }}|</h1>
      </div>
      <form>
        <div class="row calculator-value mb-4">
          <div class="col">
            <input id="input-1" v-model="estado.value1" class="form-control focus-ring focus-ring-dark border-0" type="number" placeholder="000">
            <label class="text-white text-uppercase fw-semibold d-flex justify-content-center" for="input-1">Valor-1</label>
          </div>
          <div class="col-1 text-white fs-3 text-center op">{{ estado.op }}</div>
          <div class="col">
            <input id="input-2" v-model="estado.value2" class="form-control focus-ring focus-ring-dark border-0" type="number" placeholder="000">
            <label class="text-white text-uppercase fw-semibold d-flex justify-content-center" for="input-2">Valor-2</label>
          </div>
        </div>
        <div class="row">
          <div class="col-md-12">
            <select @change="evento => estado.op = evento.target.value" class="form-control focus-ring focus-ring-dark border-0">
              <option value="+">Somar</option>
              <option value="-">Diminuir</option>
              <option value="*">Multiplicar</option>
              <option value="/">Dividir</option>
              <option value="%">Porcentagem</option>
            </select>
          </div>
          <div class="col mt-4">
            <button @click="limpaValores()" type="button" class="btn border-white text-white">C</button>
          </div>
          <div class="col">
            <h2 class="text-white m-2">{{ estado.error }}</h2>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<style>
#app {
  background-color: rgb(36, 36, 36);
}
</style>

<style scoped>
.container {
  max-width: 100%;
  width: 500px;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.calculator {
  border: 1px solid #ffffff;
  box-shadow: rgba(0, 0, 0, 0.19) 0px 10px 20px, rgba(0, 0, 0, 0.23) 0px 6px 6px;
}

.calculator-display {
  height: 90px;
  overflow-y: scroll;
  border-bottom: 1px solid #3f3f3f;
}

::-webkit-scrollbar {
  width: 0px;
}

</style>