<!-- MenuItens.vue -->
<template>
  <div class="bg-gray-100 p-6">

    <h2 class="text-2xl font-semibold mb-4 text-center m-">Cardápio</h2>

    <ul class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
      <li v-for="item in menu" :key="item.id" class="bg-white p-4 rounded-lg shadow-md">
        <!-- Adicione uma imagem aqui, substituindo '/path/to/image.jpg' pelo caminho da imagem do lanche -->
        <img :src="require(`@/assets/img/${item.image}`)" alt="Imagem do lanche" class="w-full h-32 object-cover mb-4 rounded-md">
        <p class="text-lg font-semibold">{{ item.name }}</p>
        <p class="text-gray-600">R$ {{ item.price.toFixed(2) }}</p>
        <div class="mt-4 flex justify-between">
          <button @click="adicionarAoCarrinho(item)" class="bg-blue-500 text-white px-4 py-2 rounded-md">Adicionar ao Carrinho</button>
          <button @click="removerDoCarrinho(item)" class="bg-red-500 text-white px-4 py-2 rounded-md">Remover do Carrinho</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      menu: [
      { id: 1, name: 'Hambúrguer', price: 10.99, image: 'hamburger.jpg' },
        { id: 2, name: 'Batata Frita', price: 4.99, image: 'fritas.jpg' },
        // Adicione mais itens conforme necessário
      ],
    };
  },
  methods: {
    adicionarAoCarrinho(item) {
      this.$emit('adicionar-ao-carrinho', item);
    },
    removerDoCarrinho(item) {
      this.$emit('remover-do-carrinho', item);
    },
  },
};
</script>
