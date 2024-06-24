<template>
    <div class="product-list">
        <div v-for="product in products" :key="product.id" class="product">
            <p>{{ product.title }} - ${{ product.price }}</p>
            <button @click="addToCart(product)">Add to Cart</button>
        </div>
    </div>
</template>

<script setup>
import { useCartStore } from '@/stores/cart';
import { ref, onMounted } from 'vue';

const cartStore = useCartStore();
const products = ref([]);

const fetchProducts = async () => {
    const res = await fetch('https://dummyjson.com/products');
    const data = await res.json();
    products.value = data.products;
};

const addToCart = (product) => {
    cartStore.addItem(product);
};

onMounted(fetchProducts);
</script>

<style scoped>
.product-list {
    display: flex;
    flex-wrap: wrap;
}

.product {
    margin: 10px;
    padding: 10px;
    border: 1px solid #ccc;
}
</style>