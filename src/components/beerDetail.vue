<template lang="html">
  <div>
  <h3>{{ beer.name}}</h3>
  <p>-{{ beer.tagline}}</p>
  <p>Description:{{ beer.description}}</p>
  <p>ABV:{{ beer.abv}}</p>


  <p>Yeast: {{ beer.ingredients.yeast}}</p>

  <button v-on:click="addToFave" type="button" name="addToFave" v-model="favourite">Add to favourites</button>
  </div>
</template>

<script>
export default {
  name: 'beer-detail',
  props: ['beer'],
  methods: {
    addToFave(){
      eventBus.$emit('addToFave', this.beer)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
