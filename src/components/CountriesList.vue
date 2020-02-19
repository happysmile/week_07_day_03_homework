<template lang="html">
  <ul>
    <country-list-item v-for="(country, index) in countries" v-bind:country="country" v-bind:key="index"></country-list-item>
  </ul>
</template>

<script>
import CountryListItem from './CountryListItem.vue';

export default {
  name: "countries-list",
  props: ['countries'],
  components: {
    "country-list-item" : CountryListItem
  }
}
</script>

<style lang="css" scoped>
</style>
