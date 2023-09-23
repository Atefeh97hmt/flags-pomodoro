<!-- InputField.vue -->
<template>
  <input v-model="modelValue" :type="type" :class="inputClasses" :placeholder="placeholder" class="bg-gray-100 border border-gray-300 text-gray-900 text-sm rounded-sm md:w-1/2 w-full py-2 px-1 mb-4" />
</template>

<script setup>
import { ref } from 'vue';

const modelValue = ref('');
const type = 'text';
const placeholder = '';

</script>