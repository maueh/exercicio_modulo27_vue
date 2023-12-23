<script setup>
const props = defineProps(['titulo'])
</script>

<template>
  <div class="container">
    <header class="pt-5 pb-3">
      <h1 class="text-center">{{ props.titulo }}</h1>
    </header>
  </div>
</template>
