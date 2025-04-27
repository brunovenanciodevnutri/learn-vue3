<script setup>
    const props = defineProps(['nome', 'idade', 'cidade', 'cidades', 'funcao']);
</script>

<template>
    <p>Nome: {{ nome }}</p>
    <p>Idade: {{ idade }}</p>
    <p>Cidade: {{ cidade }}</p>

    <ul>
        <li v-for="c in cidades">{{ c }}</li>
    </ul>

    <button @click="funcao">Clique aqui</button>
</template>