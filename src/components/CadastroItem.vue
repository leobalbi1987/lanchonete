<!-- CadastroItem.vue -->
<template>
  <div>
    <h2>Cadastrar Novo Item</h2>
    <form @submit.prevent="cadastrarNovoItem">
      <label>
        Nome:
        <input v-model="novoItem.name" required />
      </label>
      <label>
        Preço:
        <input v-model="novoItem.price" type="number" step="0.01" required />
      </label>
      <button type="submit">Cadastrar</button>
    </form>
  </div>
</template>

<script>



export default {
  name:'CadastroItem',
  data() {
    return {
      novoItem: {
        name: '',
        price: null,
      },
    };
  },
  methods: {
    async cadastrarNovoItem() {
      try {
        const response = await fetch('http://localhost:3000/menu', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify(this.novoItem),
        });

        if (response.status === 201) {
          // Limpar o formulário após o cadastro bem-sucedido
          this.novoItem = { name: '', price: null };
          
          // Emite um evento para informar que um novo item foi adicionado
          this.$emit('novo-item-adicionado');
        } else {
          console.error('Erro ao cadastrar novo item:', response.statusText);
        }
      } catch (error) {
        console.error('Erro ao cadastrar novo item:', error);
      }
    },
  },
};
</script>
