<template lang="html">
  <div>
    <select @change="handleChange">
      <option v-for="(country, index) in countries" :value="index" :key="index">{{country.name}}</option>
    </select>
  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'countries-select',
  props: ['countries'],
  methods: {
    handleChange(){
      eventBus.$emit('selected-country', this.countries[event.target.value])
    }
  }
}
</script>

<style lang="css" scoped>
  select {
    background-color: darkslategrey;
    color: white;
  }
</style>
