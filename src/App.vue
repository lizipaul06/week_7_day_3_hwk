<template>
  <div  >
    <h1>List of countries</h1>
    <div class="main-container">
      <countries-list :countries='countries'> </countries-list>
      <country-detail :country='countrySelected'> </country-detail>
    </div>
  </div>
</template>

<script>
import CountriesList from './components/CountriesList.vue';
import {eventBus} from './main.js'
import CountryDetail from './components/CountryDetail.vue';



export default {
  name: 'app',
  data() {
    return {
      countries: [],
      countrySelected: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(data => data.json())
    .then(countries => this.countries = countries)
    eventBus.$on('country-selected', (country) => {this.countrySelected = country;
    })

  },
  components:{
    "countries-list": CountriesList,
    "country-detail": CountryDetail
  }
}


</script>




<style>
  .main-container {
    display: flex;
    justify-content: space-between;
  }
</style>
