<script setup>
    function mensagem(){
        alert('Trabalhando com eventos de clique!');
    }
</script>

<template>
    <button @click="mensagem()">Clique aqui</button>
</template>