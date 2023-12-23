<script setup>
const props = defineProps(['atualizarNumero1', 'atualizarNumero2', 'atualizarOperador'])
</script>

<template>
  <div class="container">
    <form class="card border-light py-4 px-5 shadow-sm col-12">
      <div class="row justify-content-center">
        <label class="col-md-6 form-label">
          Operação
          <select class="form-select" @change="props.atualizarOperador">
            <option selected>Somar</option>
            <option>Subtrair</option>
            <option>Multiplicar</option>
            <option>Dividir</option>
          </select>
        </label>
      </div>
      <div class="row mt-3 justify-content-center">
        <label class="form-label col-md-6">
          Número 1
          <input
            class="form-control"
            type="number"
            @keyup="props.atualizarNumero1"
            @change="props.atualizarNumero1"
          />
        </label>
      </div>
      <div class="row mt-3 justify-content-center">
        <label class="form-label col-md-6">
          Número 2
          <input
            class="form-control"
            type="number"
            @keyup="props.atualizarNumero2"
            @change="props.atualizarNumero2"
          />
        </label>
      </div>
    </form>
  </div>
</template>
<style>
.invalido {
  color: red;
  border-color: red;
}
</style>
