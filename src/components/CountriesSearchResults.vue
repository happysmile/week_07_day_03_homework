<template lang="html">

<ul v-if="countries" >
  <li v-for="country of countries" class="country-detail">
    <h2>{{country.name}}</h2>
    <img v-bind:src="country.flag" v-bind:alt="country.name" width="300">
    <p>Capital: {{country.capital}}</p>
    <p>Population: {{country.population}}</p>
    <p v-if="country.languages">Languages:</p>
    <ul v-if="country.languages">
      <li v-for="language of country.languages">{{language.name}}</li>
    </ul>
  </li>
</ul>


</template>

<script>
export default {
  name: "countries-search-results",
  props: ['countries']
}
</script>

<style lang="css" scoped>
</style>
