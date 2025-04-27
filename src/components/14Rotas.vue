<script setup>
    import { ref, computed } from 'vue'

    import Pagina1 from './14RotasPagina1.vue' // Importando cada página
    import Pagina2 from './14RotasPagina2.vue'
    import PaginaErro from './14RotasPagina3.vue'

    const routes = { // Criando as rotas e caminhos do site.
        '/': Pagina1,
        '/pagina2': Pagina2,
        '/404': PaginaErro
    }

    const referenciaRota = ref(window.location.hash) // Obter o conteúdo a partir da cerquila, exemplo: https://localohost:5173/#/sobre.

    window.addEventListener('hashchange', () => { // Executa a ação quando realizar a navegação entre páginas.
        referenciaRota.value = window.location.hash
    });

    const currentView = computed(() => { // Função responsável por exibir a página específica.
        return routes[referenciaRota.value.slice(1) || '/'] || PaginaErro
    })
    
</script>

<template>
    <a href="#/">Página 1</a>
    |
    <a href="#/pagina2">Página 2</a>

    <component :is="currentView" /> <!-- Serve para exibir as páginas. -->
</template>