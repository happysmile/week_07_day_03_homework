<template lang="html">
  <div>
    <h1>Countries List</h1>
    <country-detail v-bind:country="selectedCountry"></country-detail>
    <countries-list v-bind:countries="countries"></countries-list>    
  </div>
</template>

<script>
import CountriesList from './components/CountriesList.vue';
import {eventBus} from './main.js';
import CountryDetail from './components/CountryDetail.vue';

export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null
    }
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(result => result.json())
    .then(countries => this.countries = countries);

    eventBus.$on('country-selected', (country) => this.selectedCountry = country)
  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail
  }
}
</script>

<style lang="css" scoped>
</style>
