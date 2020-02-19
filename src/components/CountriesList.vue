<template lang="html">
  <select v-on:change="showDetails" v-model="selectedCountry">
    <option v-for="(country, index) in countries" v-bind:value="country">{{country.name}}</option>
  </select>
</template>

<script>

import {eventBus} from '../main.js';

export default {
  name: "countries-list",
  data(){
    return {
      "selectedCountry" : {}
    }
  },
  props: ['countries'],
  methods: {
    showDetails(){
      eventBus.$emit('country-selected', this.selectedCountry)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
