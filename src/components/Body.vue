<script setup>
    const props = defineProps(['calcularResultado', 'estado']);
</script>

<template>
    <div class="card-body">
        <div class="row mb-3 mt-5">
            <div class="col-md-4">
                <input class="form-control" type="number" :value="props.estado.num1" @input="evento => props.estado.num1 = Number(evento.target.value)" placeholder="Digite o primeiro número">
            </div>

            <div class="col-md-4">
                <select class="form-select text-center" :value="props.estado.operacao" @change="evento => props.estado.operacao = evento.target.value">
                    <option value="--">Selecione o operador</option>
                    <option value="somar">SOMAR POR</option>
                    <option value="diminuir">DIMINUIR POR</option>
                    <option value="dividir">DIVIDIR POR</option>
                    <option value="multiplicar">MULTIPLICAR POR</option>
                </select>
            </div>

            <div class="col-md-4">
                <input class="form-control" type="number" :value="props.estado.num2" @input="evento => props.estado.num2 = Number(evento.target.value) " placeholder="Digite o segundo número">
            </div>
        </div>
        <div class="text-center mt-5">
            <p v-if="props.estado.erro" class="text-danger fw-bold">{{ props.estado.erro }}</p>
            <h4>Resultado: {{props.calcularResultado}}</h4>
        </div>          
    </div>
</template>

<style scoped>
    .card-body {
        background-color: #ea5df4;
    }
</style>