<script setup>
    import { onMounted, ref } from 'vue';

    let vetor = ref([]) // Vetor contendo as postagens da requisição HTTP.

    onMounted(() => {
        fetch('https://jsonplaceholder.typicode.com/posts')
        .then(retorno => retorno.json())
        .then(retorno => vetor.value = retorno)
    });
</script>

<template>

    <h1>Requisições HTTP</h1>

    <table>
        <tr v-for="v in vetor">
            <td>{{ v.userId }}</td>
            <td>{{ v.id }}</td>
            <td>{{ v.title }}</td>
            <td>{{ v.body }}</td>
        </tr>
    </table>
</template>