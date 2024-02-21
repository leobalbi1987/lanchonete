<!-- ResumoPedido.vue -->
<template>
  <div>
    <h2>Resumo do Pedido</h2>
    <ul>
      <li v-for="item in carrinho" :key="item.id">
        {{ item.name }} - R$ {{ item.price.toFixed(2) }}
      </li>
    </ul>
    <p>Total: R$ {{ calcularTotal().toFixed(2) }}</p>
    <button @click="finalizarPedido">Finalizar Pedido</button>
  </div>
</template>

<script>
export default {
  props: ['carrinho'],
  methods: {
    calcularTotal() {
      return this.carrinho.reduce((total, item) => total + item.price, 0);
    },
    finalizarPedido() {
      // Lógica para finalizar o pedido (pode ser uma chamada a uma API, etc.)
      alert('Pedido finalizado com sucesso!');
      this.$emit('limpar-carrinho');
    },
  },
};
</script>
