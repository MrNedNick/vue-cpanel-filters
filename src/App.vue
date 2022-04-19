<template>
  <v-app class="app" id="inspire">
    <all-filters />
  </v-app>
</template>

<script>
import AllFilters from "./components/AllFilters.vue";
export default {
  components: {
    AllFilters,
  },
};
</script>

<style>
.theme--light.v-application {
  background-color: #f5f6f7 !important;
}
</style>




