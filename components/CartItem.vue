<template>
    <div class="cart-item">
        <p>{{ item.title }} - ${{ item.price }} x {{ item.quantity }}</p>
        <button @click="removeItem">Remove</button>
    </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
    item: {
        type: Object,
        required: true,
    },
});

const emits = defineEmits(['remove']);

const removeItem = () => {
    emits('remove', props.item.id);
};
</script>

<style scoped>
.cart-item {
    display: flex;
    justify-content: space-between;
    margin-bottom: 10px;
}
</style>