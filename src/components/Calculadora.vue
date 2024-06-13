<template>
    <div class="calculadora">
        <div class="input-fields">
            <input type="number" v-model.number="numero1" placeholder="Número 1" />
            <select v-model="operacao">
                <option value="adicionar">+</option>
                <option value="subtrair">-</option>
                <option value="multiplicar">*</option>
                <option value="dividir">/</option>
            </select>
            <input type="number" v-model.number="numero2" placeholder="Número 2" />
        </div>
        <div class="resultado">
            <h2>Resultado: {{ resultado }}</h2>
        </div>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const numero1 = ref(0);
const numero2 = ref(0);
const operacao = ref('adicionar');

const resultado = computed(() => {
    switch (operacao.value) {
        case 'adicionar':
            return numero1.value + numero2.value;
        case 'subtrair':
            return numero1.value - numero2.value;
        case 'multiplicar':
            return numero1.value * numero2.value;
        case 'dividir':
            return numero2.value !== 0 ? numero1.value / numero2.value : 'Erro: Divisão por zero';
        default:
            return 0;
    }
});
</script>

<style scoped>

.calculadora {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 50px;
}

.input-fields {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 20px;
}

.resultado {
    font-size: 1.5em;
    font-weight: bold;
}
</style>