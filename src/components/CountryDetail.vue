<template lang="html">
  <div>
    <p><b>Name:</b> {{country.name}}</p>
    <p><b>Capital:</b> {{country.capital}}</p>
    <p><b>Population:</b> {{country.population}}</p>
  </div>
</template>

<script>

export default {
  "name": "country-detail",
  "props": ["country"]
}
</script>

<style lang="css" scoped>
div {
  background-color: darkslategrey;
  color: white;
  max-height: 8em;
  padding: 0 3em;
  border-radius: 1em;
  position: fixed;
  right: 20%;
  top: 250px;
}
</style>
