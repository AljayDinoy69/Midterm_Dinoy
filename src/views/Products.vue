<template>
  <div class="product-manager">
    <h1>Product Manager</h1>
    <ProductForm @add-product="addProduct" />
    <ProductList :products="products" @edit-product="editProduct" />
  </div>
</template>

<script>
import { reactive } from 'vue';
import ProductForm from '../components/ProductForm.vue';
import ProductList from '../components/ProductList.vue';

export default {
  components: { ProductForm, ProductList },
  setup() {
    const products = reactive([]);

    const addProduct = (product) => {
      products.push({ ...product, id: Date.now() });
    };

    const editProduct = (updatedProduct) => {
      const index = products.findIndex(p => p.id === updatedProduct.id);
      if (index !== -1) products[index] = { ...updatedProduct };
    };

    return { products, addProduct, editProduct };
  },
};
</script>

<style>
.product-manager {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

h1 {
  text-align: center;
  color: #333;
  margin-bottom: 20px;
}

.product-form {
  margin-bottom: 30px;
}

.product-list {
  margin-top: 20px;
}

@media (max-width: 600px) {
  .product-manager {
    padding: 10px;
  }

  h1 {
    font-size: 1.8rem;
  }
}
</style>
