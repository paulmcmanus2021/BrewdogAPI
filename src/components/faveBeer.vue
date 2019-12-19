<template lang="html">
  <div class="faveBeerSection">
    <h1>Your favourite Beers</h1>
    <h3 v-for="(beer, index) in beers">{{ beer.name}}</h3>
  </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: 'fave-beer',
  props: ['beers'],

  // computed: {
  //   faveBeers() {
  //     return this.beers.filter((beer) => {
  //       return beer.favourite === true
  //     })
  //   }
  // }


}
</script>

<style lang="css" scoped>
</style>
