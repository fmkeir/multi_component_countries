<template>
  <div id="app">
    <h1>Countries EventBus trip</h1>
    <div class="main-container">
      <countries-select :countries="countries" class="contained"></countries-select>
      <country-detail :country="selectedCountry" class="contained" v-if="selectedCountry"></country-detail>
    </div>
  </div>
</template>

<script>
import CountriesSelect from './components/CountriesSelect';
import CountryDetail from './components/CountryDetail';
import {eventBus} from './main.js';

export default {
  name: 'App',
  data(){
    return {
      countries: [],
      selectedCountry: null
    }
  },
  mounted(){
    fetch("https://restcountries.eu/rest/v2/all")
    .then(response => response.json())
    .then(data => this.countries = data)

    eventBus.$on('selected-country', (country) => {
      this.selectedCountry = country
    })
  },
  components: {
    "countries-select": CountriesSelect,
    "country-detail": CountryDetail
  }
}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    margin-top: 60px;
  }
  li {
    list-style: none;
  }

  .main-container {
    display: flex;
    margin-left: 15%;
  }

  h1 {
    text-align: center;
    margin-bottom: 1em;
    font-size: 60px;
  }

  .contained {
    /* width: 30%; */
  }
</style>
