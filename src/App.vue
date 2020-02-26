<template>
  <div id="app">
    <h1>Countries EventBus trip</h1>
    <div class="main-container">
      <input type="text" v-model="search" placeholder="Filter countries...">
      <countries-select :countries="filteredCountries" class="contained"></countries-select>
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
      selectedCountry: null,
      search: ''
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
  computed: {
    filteredCountries: function(){
      return this.countries.filter(country => {
        return country.name.toLowerCase().includes(this.search.toLowerCase())
      })
    }
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

  input {
    margin-right: 1em;
  }

  .contained {
    /* width: 30%; */
  }
</style>
