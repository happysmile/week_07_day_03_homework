<template lang="html">
  <input v-on:input="filterCountries(countries)" v-model="search.text" type="text">
</template>

<script>

import {eventBus} from '../main.js';

export default {

  name: 'country-search',

  data(){
    return {
      "search": {
        results: [],
        text: "" }
    }
  },

  props: ['countries'],

  methods: {
    filterCountries(countries){
      this.search.results = countries.filter(country => country.name.toLowerCase().includes(this.search.text.toLowerCase()));
      eventBus.$emit('country-searched', this.search.results);
    }
  }

}
</script>

<style lang="css" scoped>
</style>
