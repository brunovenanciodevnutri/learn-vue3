<script setup>
    import 'bootstrap/dist/css/bootstrap.min.css'
    import { onMounted, ref } from 'vue';

    // Vetor
    let produtos = ref([]);

    // Renderizando os dados da API (GET)
    onMounted(() => {
        fetch('http://localhost:3000/produtos')
        .then(requisicao => requisicao.json())
        .then(retorno => produtos.value = retorno);
    });

    // Objeto do tipo produto
    let obj = ref({'id': 0, 'produto': '', 'valor': 0});

    // Função para cadastrar
    function cadastrar(event) {
        fetch('http://localhost:3000/produtos', {
            method: 'POST',
            body: JSON.stringify(obj.value),
            headers: {'Content-Type': 'application/json'}
        })
        .then(requisicao => requisicao.json())
        .then(retorno => {
            
            // Cadastrar o produto no vetor
            produtos.value.push(retorno)

            // Limpar os inputs
            obj.value.produto = '';
            obj.value.valor = '0'
        });

        event.preventDefault(); // A página não vai dar refresh ao clicar no botão.
    }

    // Função para selecionar um produto específico
    function selecionar(indice){
        obj.value = {
            id: produtos.value[indice].id,
            produto: produtos.value[indice].produto,
            valor: produtos.value[indice].valor
        }
    }
</script>

<template>
    <form @submit="cadastrar">
        <input type="hidden" v-model="obj.id">
        <input type="text" placeholder="Produto" class="form-control" v-model="obj.produto">
        <input type="text" placeholder="Valor" class="form-control" v-model="obj.valor">
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
            <tr v-for="(p, indice) in produtos">
                <td>{{ p.produto }}</td>
                <td>{{ p.valor }}</td>
                <td><button @click="selecionar(indice)" class="btn btn-primary">Selecionar</button></td>
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