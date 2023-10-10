<template>
    <table>
        <thead>
            <tr>
                <th>Product</th>
                <th>Price</th>
                <th>Stock</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="product in products" :key="product.id" @click="$emit('row-click', product)" class="hover:bg-gray-400 hover:text-red-700">
                <td>{{ product.name }}</td>
                <td>{{ product.price }}</td>
                <td>{{ product.stock }}</td>
            </tr>
        </tbody>
    </table>
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

const products: Product[] = [
    {
        id: 1,
        name: 'Apple iPhone 12 Pro',
        description:
            'The iPhone 12 Pro is the ultimate expression of iPhone, with a 6.1-inch Super Retina XDR display, Ceramic Shield with four times better drop performance, and Pro camera system with low-light performance, telephoto lens, and LiDAR Scanner.',
        price: 999,
        image: 'https://via.placeholder.com/300x300?text=Apple+iPhone+12+Pro',
        stock: 10,
    },
    {
        id: 2,
        name: 'Samsung Galaxy S21 Ultra',
        description:
            'The Galaxy S21 Ultra is the ultimate smartphone experience, with a 6.8-inch Dynamic AMOLED 2X display, 5G connectivity, and a pro-grade camera system with 108MP sensor, 100x Space Zoom, and 8K video recording.',
        price: 1199,
        image: 'https://via.placeholder.com/300x300?text=Samsung+Galaxy+S21+Ultra',
        stock: 5,
    },
    {
        id: 3,
        name: 'Google Pixel 5',
        description:
            'The Pixel 5 is the ultimate Google phone, with a 6.0-inch OLED display, 5G connectivity, and a dual-camera system with 12.2MP sensor and 16MP ultra-wide lens. It also features a long-lasting battery and wireless charging.',
        price: 699,
        image: 'https://via.placeholder.com/300x300?text=Google+Pixel+5',
        stock: 8,
    },
];


</script>