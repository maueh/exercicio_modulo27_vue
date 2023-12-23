<script setup>
import { reactive } from 'vue'
import MeuCabecalho from './components/MeuCabecalho.vue'
import CalculadoraAritmetica from './components/CalculadoraAritmetica.vue'
import ResultadoCalculo from './components/ResultadoCalculo.vue'

const estado = reactive({
  numero1: ' ',
  numero2: ' ',
  operador: 'Somar',
  simboloOperador: '+',
  resultado: ' '
})

function atualizarNumero1(evento) {
  estado.numero1 = parseFloat(evento.target.value)
  atualizarCalculo(estado.operador)
  console.log(`${estado.numero1} = ${evento.target.value}`)
}

function atualizarNumero2(evento) {
  estado.numero2 = parseFloat(evento.target.value)
  atualizarCalculo(estado.operador)
  console.log(`${estado.numero2} = ${evento.target.value}`)
}

function atualizarOperador(evento) {
  const operador = evento.target.value
  atualizarCalculo(operador)
  console.log(`Operador: ${evento.target.value}`)
}

function atualizarCalculo(operador) {
  const { numero1, numero2 } = estado

  console.log(`${numero1} ${operador} ${numero2} =?`)
  estado.operador = operador
  switch (operador) {
    case 'Somar' || '+': {
      estado.simboloOperador = '+'
      estado.resultado = parseFloat(numero1) + parseFloat(numero2)
      break
    }
    case 'Subtrair': {
      estado.simboloOperador = '-'
      estado.resultado = numero1 - numero2
      break
    }
    case 'Multiplicar': {
      estado.simboloOperador = '×'
      estado.resultado = numero1 * numero2
      break
    }
    case 'Dividir': {
      estado.simboloOperador = '÷'
      estado.resultado = numero1 / numero2
      break
    }
    default: {
      break
    }
  }
}

function calculoValido() {
  const numero1 = parseFloat(estado.numero1)
  const numero2 = parseFloat(estado.numero2)
  console.log(isNaN(numero1))
  if (isNaN(numero1) || isNaN(numero2)) {
    return false
  } else {
    return divisaoValida(estado.operador, numero2)
  }
}

function divisaoValida(operador, divisor) {
  if (operador === 'Dividir' && divisor == 0) {
    return false
  } else {
    return true
  }
}
</script>

<template>
  <MeuCabecalho titulo="Calculadora Aritmética com Vue"></MeuCabecalho>
  <main>
    <CalculadoraAritmetica
      :atualizarNumero1="atualizarNumero1"
      :atualizarNumero2="atualizarNumero2"
      :atualizarOperador="atualizarOperador"
    ></CalculadoraAritmetica>

    <ResultadoCalculo
      v-if="calculoValido()"
      :numero1="estado.numero1"
      :numero2="estado.numero2"
      :operador="estado.simboloOperador"
      :resultado="estado.resultado"
      >fsgf</ResultadoCalculo
    >
    <div
      class="container p-5 fs-5 text-danger"
      v-else-if="!divisaoValida(estado.operador, estado.numero2)"
    >
      Não é possível dividir por zero!
    </div>
  </main>
</template>

<style scoped>
.container {
  max-width: 720px;
}
</style>
