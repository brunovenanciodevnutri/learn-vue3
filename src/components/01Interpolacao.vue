<script setup>
  let nome = 'Bruno';
  let idade = 22;
  let numero1 = 20;
  let numero2 = 10;
</script>

<template>
  <p>{{ 'Olá ' + nome + ' você tem ' + idade + ' anos.'}}</p>
  <p>{{ numero1+numero2 }}</p>
</template>