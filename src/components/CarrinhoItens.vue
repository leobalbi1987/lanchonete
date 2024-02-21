<!-- CarrinhoItens.vue -->
<template>
  <div>
    <h2>Carrinho</h2>
    <ul>
      <li v-for="item in carrinho" :key="item.id">
        {{ item.name }} - R$ {{ item.price.toFixed(2) }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['carrinho'],
};
</script>
