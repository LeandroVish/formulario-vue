<script setup>
import { ref } from 'vue'

const produtos = ref([
{
  id: 1,
  nome: 'Camiseta',
  preco: 49.90
},
{
  id: 2,
  nome: 'Calça',
  preco: 99.90
},
{
  id: 3,
  nome: 'Meia',
  preco: 9.90
},
{
  id: 4,
  nome: 'Sapato',
  preco: 199.90
},
{
  id: 5,
  nome: 'Boné',
  preco: 29.90
},
{
  id: 6,
  nome: 'Óculos',
  preco: 99.90
},
{
  id: 7,
  nome: 'Relógio',
  preco: 299.90
},
{
  id: 8,
  nome: 'Bermuda',
  preco: 79.90
},
{
  id: 9,
  nome: 'Cueca',
  preco: 19.90
}
])

const carrinho = ref({
  items: [
{
  id: 1,
  nome: 'Camiseta',
  preco: 49.90,
  quantidade: 1,
  valorTotal: 49.90
},
{
  id: 2,
  nome: 'Calça',
  preco: 99.90,
  quantidade: 2,
  valorTotal: 199.80
},
{
  id: 3,
  nome: 'Meia',
  preco: 9.90,
  quantidade: 4,
  valorTotal: 39.60
}
]
total: 288.30
})

function remover(index) {
  carrinho.value.splice(index, 1);
}
function adicionar(index) {
  if(produtos.value[index].quantidade > 0){

    novoItem.value.id = produtos.value[index].id;
    novoItem.value.nome = produtos.value[index].nome;
    novoItem.value.preco = produtos.value[index].preco;
    novoItem.value.quantidade = produtos.value[index].quantidade;
  } else {
    alert("Escolha uma quantidade do produto que você dejesa")
  }
}
function desconto(id) {
  if (produtos.value[id].quantidade > 0) {
    produtos.value[id].quantidade--;
  }
}
</script>

<template>
  <div class="geral">
    <div class="listaProdutos">
      <h2>Lista de Produtos</h2>
      <div class="margemLista">
        <div class="itens" v-for="(produt, index) in produtos" :key="index">
          <p>Nome: {{ produtos.nome }}</p>
          <p>Preço: R$ {{ produtos.preco }}</p>
          <p>Quantidade: {{ produtos.quantidade }}</p>
          <button @click="produtos.quantidade++">Add</button>
          <button @click="desconto(produtos.id - 1)">Rmv</button>
        </div>
      </div>
    </div>
  </div>

  <div class="carrinho">
    <h2>Carrinho</h2>
    <div class="itens" v-for="(produto, index) in carrinho" :key="index">
      <p>Nome: {{ produto.nome }}</p>
      <p>Preço: {{ produto.preco }}</p>
      <p>Quantidade: {{ produto.quantidade }}</p>
      <button @click="remover(index)">Rmv</button>
    </div>
  </div>
</template>

<style scoped>
.listaProdutos {
  text-align: auto;
  margin: 15px;
  margin-top: 15px;
  width: auto;
  height: auto;
  border-radius: 10px;
  color: black;
}
.carrinho {
  text-align: auto;
  margin: 15px;
  margin-top: 15px;
  width: auto;
  height: auto;
  border-radius: 10px;
  color: black;
}
.margemLista {
display: flex;
flex-direction: row;
flex-wrap: wrap;
}
.itens {
  width: 150px;
  padding: 20px;
  background-color: dodgerblue;
  margin: 10px;
  border-radius: 7px;
}
.geral {
  display: grid;
  grid-template-columns: auto;
}
h1, h2 {
  margin-top: 0;
  padding: 10px;
  font-size: 25px;
  color: rgb(224, 44, 44);
}
button {
  margin: 3px;
  font-size: 14px;
  background-color: gray;
  color: aliceblue;
  border-radius: 5px;
  padding: 5px 10px;
}
</style>
