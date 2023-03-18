<template>
    <DataTable :value="countriesData" paginator :rows="5" v-if="countriesData.length" class="countries-table">
        <Column field="code" header="Code"></Column>
        <Column field="name" header="Name"></Column>
        <Column field="flag" header="Flag">
            <template #body="slotProps">
                <img :src="'src/assets/flags/'+slotProps.data.flag"
                    alt="Flag of country" class="w-6rem shadow-2 border-round" />
            </template>
        </Column>
    </DataTable>
    <h2 v-else> No country found. </h2>
</template>

<script setup>

import DataTable from 'primevue/datatable'
import Column from 'primevue/column'

defineProps({
    countriesData: {
        type: [Array, Object],
        required: true
    }
})

</script>

<style>

.countries-table {
    text-align: center;
    margin: 0 0.5rem;
}

.countries-table img {
    width: 4rem;
}

</style>