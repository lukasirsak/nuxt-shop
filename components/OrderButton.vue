<template>
    <button type="button"
            @click="emit('orderChanged', field)"
            class="inline-flex items-center rounded-md px-3 py-2 text-sm font-semibold shadow-sm"
            :class="{
                'bg-white text-gray-900 ring-1 ring-inset ring-gray-300 hover:bg-gray-50': field != activeOrder,
                'bg-indigo-600 text-white hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600': field == activeOrder
            }">
        <slot/>
    </button>
</template>

<script lang="ts" setup>
import type { OrderValue } from '@/types/OrderValue.js';

const props = defineProps({
    field: {
        required: true,
        type: String as PropType <OrderValue>,
    },
    activeOrder: {
        required: true,
        type: String as PropType <OrderValue>,
    }
});

const emit = defineEmits(['orderChanged']);
</script>