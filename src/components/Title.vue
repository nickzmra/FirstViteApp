<template>
    <h1 class="text-6xl text-gray-700 font-light text-center">{{msg}}</h1>
</template>

<script setup>
import {defineProps} from 'vue'

defineProps({
    msg: {
        type: String,
        default: 'to Do',
    },
})
</script>