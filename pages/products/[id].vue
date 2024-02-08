<template>
    <div class="mx-auto max-w-xl my-8">
        <div class="group">
        <div class="aspect-h-1 aspect-w-1 w-full overflow-hidden rounded-lg bg-gray-200 xl:aspect-h-4 xl:aspect-w-7">
            <img :src="product.image" class="h-full w-full object-cover object-center group-hover:opacity-75" />
        </div>
        <h3 class="mt-4 text-sm text-gray-700">{{ product.title }}</h3>
        <p class="mt-1 text-lg font-medium text-gray-900">{{ product.price }}</p>
        </div>
    </div>
</template>

<script lang="ts" setup>
  const endpoint = "https://fakestoreapi.com/products/" + useRoute().params.id;
  const { data: product, error } = await useFetch(endpoint); 

  if (error.value) {
    console.log(error.value);
  }
</script>