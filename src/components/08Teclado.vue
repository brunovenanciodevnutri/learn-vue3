<script setup>
    function mensagem(){
        alert('Executando a função!')
    }
</script>

<template>
    <input type="text" @keyup.enter="mensagem">
</template>