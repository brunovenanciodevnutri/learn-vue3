<script setup>
    import 'bootstrap/dist/css/bootstrap.min.css'
    import { onMounted, ref } from 'vue';

    let produtos = ref([]);

    onMounted(() => {
        fetch('http://localhost:3000/produtos')
        .then(requisicao => requisicao.json())
        .then(retorno => produtos.value = retorno);
    });
</script>

<template>
    <form>
        <input type="text" placeholder="Produto" class="form-control">
        <input type="text" placeholder="Valor" class="form-control">
        <input type="submit" value="Cadastrar" class="btn btn-primary">
    </form>

    <table class="table table-striped">
        <thead>
            <tr>
                <th>Produto</th>
                <th>Valor</th>
                <th>Selecionar</th>
            </tr>
        </thead>

        <tbody>
            <tr v-for="p in produtos">
                <td>{{ p.produto }}</td>
                <td>{{ p.valor }}</td>
                <td><button class="btn btn-primary">Selecionar</button></td>
            </tr>
        </tbody>
    </table>
</template>

<style scoped>
    form {
        width: 50%;
        margin: 30px auto;
        text-align: center;
    }

    input {
        margin-bottom: 10px;
    }
</style>