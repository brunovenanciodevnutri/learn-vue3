<script setup>
    let validacao = true;
</script>

<style>
    .ok {
        color: green;
    }

    .erro {
        color: red;
    }
</style>

<template>
    <p :class="validacao ? 'ok' : 'erro'">Utilizando a diretiva class</p>
</template>