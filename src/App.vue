<template>
  <v-app id="inspire">
    <all-filters />
    <div class="submit-container">
      <v-btn class="apply-btn">SUBMIT</v-btn>
    </div>
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

<style scoped>
.submit-container {
  margin:0px auto;
}
</style>


