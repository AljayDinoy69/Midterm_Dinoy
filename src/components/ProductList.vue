<template>
  <div class="product-list">
    <h2>Product List</h2>
    <ul>
      <li v-for="product in products" :key="product.id" class="product-item">
        <div class="product-info">
          <div v-if="editingId !== product.id">
            <strong>{{ product.name }}</strong> - ${{ product.price }}
          </div>
          <div v-else>
            <input v-model="editedProduct.name" placeholder="Product Name" />
            <input v-model.number="editedProduct.price" type="number" placeholder="Price" />
            <textarea v-model="editedProduct.description" placeholder="Description"></textarea>
            <button @click="saveProduct" class="save-button">Save</button>
          </div>
        </div>
        <div class="button-group">
          <button v-if="editingId !== product.id" @click="startEditing(product)" class="edit-button">Edit</button>
          <button v-if="editingId !== product.id" @click="deleteProduct(product.id)" class="delete-button">Delete</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import { reactive, ref } from 'vue';

export default {
  props: ['products'],
  emits: ['edit-product', 'delete-product'],
  setup(_, { emit }) {
    const editingId = ref(null);
    const editedProduct = reactive({});

    const startEditing = (product) => {
      editingId.value = product.id;
      Object.assign(editedProduct, product);
    };

    const saveProduct = () => {
      emit('edit-product', { ...editedProduct });
      editingId.value = null;
    };

    const deleteProduct = (id) => {
      emit('delete-product', id);
    };

    return { editingId, editedProduct, startEditing, saveProduct, deleteProduct };
  },
};
</script>

<style>
.product-list {
  margin-top: 20px;
}

h2 {
  text-align: center;
  color: #333;
  margin-bottom: 15px;
}

ul {
  list-style: none;
  padding: 0;
}

.product-item {
  background-color: #f1f1f1;
  margin: 10px 0;
  padding: 15px;
  border-radius: 5px;
  display: flex;
  justify-content: space-between; 
  align-items: center;
}

.product-info {
  flex-grow: 1; 
}

.button-group {
  display: flex;
  gap: 10px; 
}

.edit-button, .save-button, .delete-button {
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 8px 12px;
  cursor: pointer;
}

.edit-button:hover, .save-button:hover, .delete-button:hover {
  background-color: #45a049;
}

.delete-button {
  background-color: #f44336; 
}

.delete-button:hover {
  background-color: #e53935; 
}

input, textarea {
  margin-right: 10px;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 100%;
}

textarea {
  resize: none;
  height: 60px;
}

@media (max-width: 600px) {
  .product-item {
    flex-direction: column;
    align-items: flex-start;
  }

  input, textarea {
    margin-bottom: 10px;
  }
}
</style>
