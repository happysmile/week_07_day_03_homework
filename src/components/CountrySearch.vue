<template lang="html">
  <input v-on:input="findCountry(countries)" v-model="search.text" type="text">
</template>

<script>

import {eventBus} from '../main.js';

export default {

  name: 'country-search',

  data(){
    return {
      "search": {
        result: {},
        text: "" }
    }
  },

  props: ['countries'],

  methods: {
    findCountry(countries){
      this.search.result = countries.find(country => country.name.includes(this.search.text));
      eventBus.$emit('country-searched', this.search.result)
    }
  }

}
</script>

<style lang="css" scoped>
</style>
