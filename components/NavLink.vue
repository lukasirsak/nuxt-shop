<template>
    <NuxtLink :to="to"
              :class="{
                'bg-gray-900 text-white rounded-md px-3 py-2 text-sm font-medium': isActive(to),
                'text-gray-300 hover:bg-gray-700 hover:text-white rounded-md px-3 py-2 text-sm font-medium': !isActive(to)
              }">
        <slot/>
    </NuxtLink>
</template>


<script lang="ts" setup>
    const props = defineProps({
        "to": {
            type: String,
            required: true,
        },
    });

    const isActive = (linkPath: string) => {
        return linkPath === useRoute().path;
    };
</script>