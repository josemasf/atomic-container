<template>
    <div class="flex flex-col md:flex-row">
        <div class="md:w-1/2">
            <img :src="product.image" :alt="product.name" class="w-full" />
        </div>
        <div class="md:w-1/2 md:pl-8">
            <h1 class="text-2xl font-bold mb-2">{{ product.name }}</h1>
            <p class="text-gray-400 text-base mb-4">{{ product.description }}</p>
            <p class="text-gray-400 text-base mb-4">Price: {{ product.price }}</p>
            <p class="text-gray-400 text-base mb-4">Stock: {{ product.stock }}</p>
            <button
                class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded"
                @click="close"
            >
                Close
            </button>
        </div>
    </div>
</template>

<script setup lang="ts">
interface Product {
    id: number;
    name: string;
    description: string;
    price: number;
    image: string;
    stock: number;
}

const props = defineProps<{
    product: Product;
}>();

const emits = defineEmits(['close']);

const product = props.product;

function close() {
    emits('close');
}
</script>