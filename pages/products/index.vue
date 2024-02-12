<template>
    <div class="bg-white">
        <div class="mx-auto max-w-2xl px-4 py-16 sm:px-6 sm:py-24 lg:max-w-7xl lg:px-8">
            <h2 class="sr-only">Products</h2>

            <div class="mb-4 flex gap-4 items-center justify-end">
                <OrderButton @order-changed="setActiveOrder" :active-order="activeOrder" field="price">
                Order by price
                </OrderButton>

                <OrderButton @order-changed="setActiveOrder" :active-order="activeOrder" field="title">
                Order by name
                </OrderButton>
            </div>

            <div class="grid grid-cols-1 gap-x-6 gap-y-10 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 xl:gap-x-8">
                <NuxtLink v-for="product in orderedProducts" :key="product.id" :to="'/products/' + product.id" class="group">
                    <div class="aspect-h-1 aspect-w-1 w-full overflow-hidden rounded-lg bg-gray-200 xl:aspect-h-8 xl:aspect-w-7">
                    <img :src="product.image" class="h-full w-full object-cover object-center group-hover:opacity-75" />
                    </div>
                    <h3 class="mt-4 text-sm text-gray-700">{{ product.title }}</h3>
                    <p class="mt-1 text-lg font-medium text-gray-900">{{ product.price }}</p>
                </NuxtLink>
            </div>
        </div>
    </div>
</template>

<script lang="ts" setup>
import type { AsyncData } from 'nuxt/app';
import type { FetchError } from 'ofetch';
import type { Product } from '@/types/Product';
import type { OrderValue } from '@/types/OrderValue';

const endpoint = "https://fakestoreapi.com/products";
const { data: products, error } = await useFetch(endpoint) as AsyncData<Product[], FetchError>;

if (error.value) {
    console.log(error.value);
}

const activeOrder = ref<OrderValue>('title');

const setActiveOrder = (newValue: OrderValue) => {
  activeOrder.value = newValue;
}

const orderedProducts = computed<Product[]>(() => {
    return [...products.value].sort((a, b) => {
        return a[activeOrder.value] > b[activeOrder.value] ? 1 : -1;
    });
});
</script>