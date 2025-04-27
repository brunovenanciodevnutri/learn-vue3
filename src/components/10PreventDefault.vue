<script setup>
    function validaFormulario(event){
        alert('Formulário enviado!');

        event.preventDefault(); // O "action" no form só será redirecionado se todos os campos estiverem preenchidos por conta da função event.
    }
</script>

<template>
    <form action="www.google.com.br" @submit="validaFormulario">
        <input type="submit" value="Enviar formulário">
    </form>
</template>