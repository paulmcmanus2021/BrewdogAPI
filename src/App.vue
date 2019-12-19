<template lang="html">
  <div >
    <h1>Brewdog Beers</h1>
    <div class="main-container">
      <beer-list v-bind:beers="beers"></beer-list>
      <beer-detail class="beerdetails" v-bind:beer='selectedBeer' v-if="selectedBeer"></beer-detail>
    </div>
      <fave-beer v-bind:beers="faveBeers" class="favebeers"></fave-beer>
  </div>
</template>

<script>
import FaveBeer from './components/faveBeer.vue';
import BeerList from './components/BeerList.vue';
import BeerDetail from './components/beerDetail.vue';
import { eventBus } from './main.js'

export default {
  name: 'app',
  data() {
    return {
      beers: [],
      faveBeers: [],
      selectedBeer: null,
    }
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beer => this.beers = beer)

    eventBus.$on('addToFave', (selectedBeer) => {
      selectedBeer.favourite = true;

      this.faveBeers = this.beers.filter((beer) => {
        return beer.favourite === true
      })
    }),

    eventBus.$on('beer-selected', (beer) =>{
      this.selectedBeer = beer

    })

  },
  components: {
    "fave-beer": FaveBeer,
    "beer-list" : BeerList,
    "beer-detail": BeerDetail
  }
}
</script>

<style lang="css" scoped>
  .main-container {
      display: flex;
      justify-content: space-between;
    }

  .beerdetails {
    width: 200px;
  }


</style>
