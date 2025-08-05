<script setup>
  import { reactive } from 'vue'
  import CardHeader from './components/Header.vue'
  import CardBody from './components/Body.vue'
  import CardFooter from './components/Footer.vue'
  import 'bootstrap/dist/css/bootstrap.min.css'
  const estado = reactive({
    num1: '',
    num2: '',
    operacao: '--',
    erro: '',
  })

  function calcularResultado() {
    estado.erro = ''
    const { num1, num2, operacao } = estado

    switch (operacao) {
      case '--':
        estado.erro = 'É preciso selecionar um operador'
        return 'Erro'
      case 'somar':
        return num1 + num2;
      case 'diminuir':
        return num1 - num2;
      case 'dividir':
        if (num2 === 0) {
          estado.erro = 'Não é possível dividir por zero.'
          return 'Erro'
        }
        return num1 / num2;
      case 'multiplicar':
        return num1 * num2;
      default:
        estado.erro = 'Operação inválida.'
        return 'Erro'  
    }
  }
</script>
<template>
  <div class="container mt-5">
    <div class="card shadow bg-light">
      <CardHeader />
      <CardBody :calcular-resultado="calcularResultado()" :estado="estado"/>
      <CardFooter />
    </div>
  </div>
</template>