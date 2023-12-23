<script setup>
const props = defineProps(['numero1', 'numero2', 'operador', 'resultado'])
</script>

<template>
  <div class="container">
    <div class="d-flex mt-5 mb-3 fs-5 fw-bold justify-content-center">Resultado:</div>
    <div class="d-flex flex-row justify-content-center">
      <div class="p-3 text-center fs-3 me-1 rounded-2 border border-dark-subtle">
        {{ props.numero1 }}
      </div>
      <div class="p-3 text-center fs-3 me-1">
        {{ props.operador }}
      </div>

      <div class="p-3 text-center fs-3 me-1 rounded-2 border border-dark-subtle">
        {{ props.numero2 }}
      </div>
      <div class="p-3 text-center fs-3 me-1">=</div>
      <div class="p-3 text-center fs-3 me-1 rounded-2 border border-dark-subtle">
        {{ props.resultado }}
      </div>
    </div>
  </div>
</template>

<style>
.operando-1 {
  border: 1px solid #ccc;
}
</style>
