<template lang="html">
  <li @click="handleClick">{{country.name}}</li>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'list-item',
  props: ['country'],
  methods: {
    handleClick(){
      eventBus.$emit('selected-country', this.country)
    }
  }
}
</script>

<style lang="css" scoped>
li {
  margin: 1em;
  padding: 1em;
  background-color: darkslategrey;
  color: white;
  border-radius: 1em;
  text-align: center;
}
</style>
