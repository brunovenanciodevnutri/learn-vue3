<script setup>
    let nomes = ['Alice', 'Bruna', 'Caio', 'Daniel', 'Ellen'];
</script>

<template>
    <ul>
        <li v-for="nome in nomes">{{ nome }}</li>
    </ul>
</template>