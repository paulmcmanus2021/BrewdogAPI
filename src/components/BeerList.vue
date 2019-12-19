<template lang="html">
  <div>
    <ul>
      <beer-item v-for="(beer, index) in beers" v-bind:beer="beer" v-bind:key="index"></beer-item>
    </ul>
  </div>
</template>

<script>
import BeerItem from './BeerItem.vue'

export default {
  name: 'beer-list',
  props: ['beers'],
  components: {
    "beer-item" : BeerItem
  }
}

</script>

<style lang="css" scoped>
</style>
