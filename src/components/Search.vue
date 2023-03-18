<template>
    <form @submit.prevent>
        <div class="search-container">
            <span class="p-input-icon-left">
                <i class="pi pi-search" />
                <InputText placeholder="Search by country" v-model="search" @input="$emit('highlight-user', $event)"/>
            </span>
        </div>
    </form>
</template>

<script setup>

import { ref } from "vue";

import InputText from "primevue/inputtext";

const search = ref('')

const emitEvent = defineEmits(["highlight-user"])

defineProps({

    countriesData: {
        type: Array,
        required: true,
    }
  
})

</script>

<style>
.search-container {
    display: flex;
    column-gap: 1rem;
}
</style>