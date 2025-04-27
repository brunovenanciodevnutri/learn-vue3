<script setup>
    import Exemplo13PropsDinamics2 from './13PropsDinamics2.vue'

    let cidade = 'São Paulo';
    let cidades = ['São Paulo', 'Rio de Janeiro', 'Curitiba', 'Florianópolis'];

    function mensagem(){
        alert('Função criada no componente: 13PropsDinamics2.')
    }
</script>

<template>
    <Exemplo13PropsDinamics2 nome="Ralf" idade="22" :cidade="cidade" :cidades="cidades" :funcao="mensagem"></Exemplo13PropsDinamics2>
</template>