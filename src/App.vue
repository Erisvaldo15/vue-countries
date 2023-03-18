<template>
    <main>
        <div class='container'>
            <SearchVue :countries-data="data" @highlight-user='highlightUser' />
            <Table :countries-data="data" />
        </div>
    </main>
</template>

<script setup>

import { reactive, ref, onMounted } from 'vue'

import countries from '../data.json'

import SearchVue from './components/Search.vue'
import Table from './components/Table.vue';

let data = ref([])

onMounted(() => {
    data.value = countries
})

const highlight = ref('')

function highlightUser(event) {

    let filteredCountries = reactive([])
    let search = event.target.value.toLowerCase()

    if (search) {
        data.value = countries
        filteredCountries = data.value.filter(country => country.name.toLowerCase().startsWith(search))
        data.value = filteredCountries
    } else {
        data.value = countries
    }

}

</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

main {
    height: 100vh;
}

.container {
    display: flex;
    flex-flow: column wrap;
    justify-content: space-evenly;
    align-items: center;
    height: 100%;
}

.container ul li.activated {
    background-color: chocolate;
}
</style>