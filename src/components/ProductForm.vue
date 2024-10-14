<template>
  <div class="product-form">
    <h2>Add a New Product</h2>
    <form @submit.prevent="submitForm">
      <input v-model="product.name" placeholder="Product Name" required />
      <input v-model.number="product.price" placeholder="Price" type="number" required />
      <textarea v-model="product.description" placeholder="Description"></textarea>
      <button type="submit">Add Product</button>
    </form>
  </div>
</template>

<script>
import { reactive } from 'vue';

export default {
  emits: ['add-product'],
  setup(_, { emit }) {
    const product = reactive({ name: '', price: 0, description: '' });

    const submitForm = () => {
      emit('add-product', { ...product });
      product.name = '';
      product.price = 0;
      product.description = '';
    };

    return { product, submitForm };
  },
};
</script>

<style>
.product-form {
  background-color: #f9f9f9;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
}

h2 {
  text-align: center;
  color: #333;
  margin-bottom: 15px;
}

form {
  display: flex;
  flex-direction: column;
}

input, textarea {
  margin-bottom: 15px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 1rem;
}

input:focus, textarea:focus {
  border-color: #4CAF50;
  outline: none;
}

button {
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 10px;
  cursor: pointer;
  font-size: 1rem;
}

button:hover {
  background-color: #45a049;
}

@media (max-width: 600px) {
  .product-form {
    padding: 15px;
  }

  h2 {
    font-size: 1.5rem;
  }

  input, textarea {
    font-size: 0.9rem;
  }

  button {
    font-size: 0.9rem;
  }
}
</style>
