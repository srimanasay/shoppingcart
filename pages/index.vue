<template>
    <div class="home">
        <h1>Welcome to Nuxt Shop</h1>
        <ProductList />
        <Cart />
    </div>
</template>

<script setup>
import ProductList from '@/components/ProductList.vue';
import Cart from '@/components/Cart.vue';
</script>