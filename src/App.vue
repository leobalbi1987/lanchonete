<!-- App.vue -->
<template>
  <div>
    <MenuItens @adicionar-ao-carrinho="adicionarAoCarrinho" @remover-do-carrinho="removerDoCarrinho" />
    <!-- <CarrinhoItens :carrinho="carrinho" /> -->
    <ResumoPedido :carrinho="carrinho" @limpar-carrinho="limparCarrinho" />

    <CadastroItem @novo-item-adicionado="atualizarMenu" />
    
  </div>

</template>

<script>

import MenuItens from './components/MenuItens';
// import CarrinhoItens from './components/CarrinhoItens.vue';
import ResumoPedido from './components/ResumoPedido.vue';
import CadastroItem from './components/CadastroItem.vue';

export default {
  components: {
    MenuItens,
    // CarrinhoItens,
    ResumoPedido,
    CadastroItem,
    
  },
  data() {
    return {
      carrinho: [],
    };
  },


  methods: {
    adicionarAoCarrinho(item) {
      this.carrinho.push(item);
    },

    removerDoCarrinho(item) {
      const index = this.carrinho.findIndex((c) => c.id === item.id);
      if (index !== -1) {
        this.carrinho.splice(index, 1);
      }
    },
  },
};
</script>
