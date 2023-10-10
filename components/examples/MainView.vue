<template>
    <div class="bg-gray-700">
        <table-container @row-click="rowClickHandler" v-if="showDetail===false"/>
        <product-container :product="selectedProduct" @close="closeProduct" v-else  />
    </div>
</template>

<script lang="ts" setup>
import {  ref } from 'vue';

import TableContainer from './TableContainer.vue';
import ProductContainer from './ProductContainer.vue';

interface Product {
    id: number;
    name: string;
    price: number;
    stock: number;
}

const showDetail = ref(false);

const rowClickHandler = (product: Product) => {    
    selectedProduct.value = product;
    showDetail.value = true;
};

function closeProduct() {
    showDetail.value = false;
    }

const selectedProduct = ref<Product>({
        id: 1,
        name: 'Product 1',
        price: 10.99,
        stock: 5,
    });

</script>