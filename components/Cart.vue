<template>
    <div class="cart">
        <h2>Shopping Cart</h2>
        <CartItem v-for="item in cartItems" :key="item.id" :item="item" @remove="removeItem" />
        <p>Total Items: {{ itemCount }}</p>
        <p>Total Price: ${{ totalPrice.toFixed(2) }}</p>
        <button @click="clearCart">Clear Cart</button>
    </div>
</template>

<script setup>
import { useCartStore } from '@/stores/cart';
import { computed } from 'vue';
import CartItem from '@/components/CartItem.vue';

const cartStore = useCartStore();

const cartItems = computed(() => cartStore.items);
const itemCount = computed(() => cartStore.itemCount);
const totalPrice = computed(() => cartStore.totalPrice);

const removeItem = (productId) => {
    cartStore.removeItem(productId);
};

const clearCart = () => {
    cartStore.clearCart();
};
</script>

<style scoped>
.cart {
    margin-top: 20px;
}
</style>