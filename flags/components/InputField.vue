<!-- InputField.vue -->
<template>
  <input v-model="localModelValue" :type="type" :placeholder="placeholder" class="bg-gray-100 border border-gray-300 text-gray-900 text-sm rounded-sm md:w-1/2 w-full py-2 px-1 mb-4" />
</template>

<script setup>
import { string, oneOfType, number } from 'vue-types'
const props = defineProps({
  placeholder:string(),
  type:string(),

})

const { localModelValue } = useLocalModelValue({ props})
</script>