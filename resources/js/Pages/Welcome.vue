<script setup>
import { Head, Link } from '@inertiajs/inertia-vue3';
import {Inertia} from "@inertiajs/inertia";

defineProps({
    products: Object,
});

function remove(id) {
    Inertia.delete(`api/product/remove/${id}`);
}
</script>

<template>
    <div>
    <Head title="Products" />

    <div class="mx-auto max-w-7xl my-24">
        <div class="grid md:grid-cols-3 gap-24 justify-items-center">
            <div v-for="product in products" :key="product.id" class="flex flex-col items-center gap-y-5">
                <img :src="product.image" alt="" />
                <span class="font-bold">{{ product.name }} | {{ product.price }}</span>
                <button @click="remove(product.id)" class="bg-red-400 rounded-md text-white p-4" type="button">Delete</button>
            </div>
        </div>
    </div>
    </div>
</template>
