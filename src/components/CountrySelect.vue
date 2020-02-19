
<template lang="html">

  <select id="countries" v-if="countries" v-model ="selectedCountry">
    <option v-for="country in countries" :country="country" :key="countries">{{ country.name }}</option>
  </select>

</template>

<script>
import { eventBus } from '../main.js'
export default {
  name:"country-select",
  props: [' countries ']
}
</script>

<style lang="css" scoped>
</style>
