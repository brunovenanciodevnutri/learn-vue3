<script setup>
    import { ref } from 'vue';
    const resultado = ref(null)
    const peso = ref('')
    const altura = ref('')
    
    function calcular() {
        resultado.value = (peso.value / altura.value ** 2).toFixed(2)
    }
</script>

<template>
    <div class="container">
        <h1>Calculadora IMC</h1>
        <input type="number" name="Peso" id="" placeholder="Peso (kg)" v-model.number="peso">
        <input type="number" name="Altura" id="" placeholder="Altura (m)" v-model.number="altura">

        <button id="submit" @click="calcular">Calcular</button>

        <div v-if="resultado !== null" class="resultados">
            <p>Seu IMC é {{ resultado }} de kg/m².</p>
            <p v-if="resultado > 29.9">Obesidade</p>
            <p v-else-if="resultado > 24.9 & resultado < 30">Sobrepeso</p>
            <p v-else-if="resultado >= 18.5 & resultado < 25">Eutrofia</p>
            <p v-else-if="resultado < 18.5">Magreza</p>
        </div>
    </div>
</template>

<style scoped>
    .container {
        background-color: rgb(43, 43, 43);
        width: 600px;
        height: 300px;
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 20px;
        border-radius: 8%;
    }

    h1 {
        font-family: Poppins;
        color: white;
        text-align: center;
    }

    form {
        margin-top: 10px;
    }

    input {
        padding: 5px;
        margin-top: 10px;
    }

    #submit {
        font: 11pt Poppins;
        font-weight: 600;
        color: rgb(0, 0, 0);
        background-color: rgb(255, 255, 255);
        margin-top: 15px;
    }

    #submit:hover {
        background-color: rgba(255, 255, 255, 0.753);
    }

    .resultados {
        margin-top: 15px;
        font-family: Poppins;
        color: white;
        line-height: 8px;
        text-align: center;
    }
</style>