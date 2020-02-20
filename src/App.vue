<template lang="html">
  <div>
    <h1>Countries List</h1>
    <country-search v-bind:countries="countries"></country-search>
    <countries-list v-bind:countries="countries"></countries-list>
    <country-detail v-if="selectedCountry" v-bind:country="selectedCountry"></country-detail>
    <countries-search-results v-if="filteredCountries" v-bind:countries="filteredCountries"></countries-search-results>
  </div>
</template>

<script>
import CountriesList from './components/CountriesList.vue';
import {eventBus} from './main.js';
import CountryDetail from './components/CountryDetail.vue';
import CountrySearch from './components/CountrySearch.vue';
import CountriesSearchResults from './components/CountriesSearchResults.vue';

export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null,
      filteredCountries: []
    }
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(result => result.json())
    .then(countries => this.countries = countries);
    eventBus.$on('country-selected', (country) => this.selectedCountry = country);
    eventBus.$on('country-searched', (countries) => this.filteredCountries = countries);
  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail,
    "country-search": CountrySearch,
    "countries-search-results": CountriesSearchResults
  }
}
</script>

<style lang="css" scoped>
</style>
