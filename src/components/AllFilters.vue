<template>
  <div class="wrapper">
    <div class="container">
      <advanced-filter />
      <position-filter />
      <volume-filter />
      <cpc-filter />
      <word-count-filter />
      <groupings-filter />
      <competitor-filter />
      <!-- <alternative-volume-filter /> -->
      <div class="submit-container">
        <v-btn
          @click="submit()"
          class="submit-btn apply-btn mt-4"
        >
          SUBMIT
        </v-btn>
      </div>
    </div>
  </div>
</template>

<script>
import AdvancedFilter from "./Filters/AdvancedFilter.vue";
import AlternativeVolumeFilter from "./Filters/AlternativeVolumeFilter.vue";
import CompetitorFilter from "./Filters/CompetitorFilter.vue";
import CpcFilter from "./Filters/CpcFilter.vue";
import GroupingsFilter from "./Filters/GroupingsFilter.vue";
import PositionFilter from "./Filters/PositionFilter.vue";
import VolumeFilter from "./Filters/VolumeFilter.vue";
import WordCountFilter from "./Filters/WordCountFilter.vue";
export default {
  components: {
    AdvancedFilter,
    GroupingsFilter,
    PositionFilter,
    VolumeFilter,
    CpcFilter,
    WordCountFilter,
    CompetitorFilter,
    AlternativeVolumeFilter,
  },
  data: () => ({
    advancedFilter: "",
    postionFilter: "",
    volumeFilter: "",
    cpcFilter: "",
    wordCountFilter: "",
    groupingsFilter: "",
    competitorFilter: "",
  }),
  methods: {
    submit() {},
  },
};
</script>


<style lang='scss'>
body {
  font-family: "Source Sans Pro";
  font-weight: 400;
  font-size: 14px;
  color: #05122d;
}
.wrapper {
  margin: 0px auto;
  background-color: #f5f6f7;
  width: 800px;
  min-height: 300px;
  margin-top: 100px;
}
.container {
  display: flex;
  flex-wrap: wrap;
}
.menu-container {
  margin-left: 40px;
  margin-top: 40px;
}
.advanced-container {
  display: flex;
  height: 40px !important;
}

.main-btn.v-btn:not(.v-btn--round).v-size--default {
  width: 200px;
}
.menu {
  max-width: 201px;
  margin-top: -24px;
}
.menu .v-list-item {
  padding: 0;
}
.radio {
  margin-top: 0px;
  padding: 8px 0px 8px 12px;
  width: 201px;
}
.radio:hover {
  background-color: rgba(235, 235, 235, 0.726);
}
.v-input--radio-group--column .v-radio:not(:last-child):not(:only-child) {
  margin-bottom: 0px;
}

.theme--light.v-label {
  color: #05122d !important;
}
.custom-section {
  display: flex;
}
.custom-line {
  padding-top: 37px;
}
.section-label {
  font-family: "Source Sans Pro";
  font-weight: 400;
  font-size: 14px;
  line-height: 166%;
  color: #05122d;
  opacity: 0.4;
  margin-left: 16px;
  margin-top: -40px;
}
.v-text-field--filled > .v-input__control > .v-input__slot,
.v-text-field--full-width > .v-input__control > .v-input__slot,
.v-text-field--outlined > .v-input__control > .v-input__slot {
  min-height: 0px !important;
  max-width: 200px !important;
  height: 50px;
  border-radius: 6px;
}
.v-text-field fieldset, .v-text-field .v-input__control {
    /* height: 45px; */
}
// Select Input Title
.select .v-text-field--full-width .v-input__prepend-inner,
.v-text-field--enclosed .v-input__prepend-inner {
  margin-top: 12px !important;
}
// Select Cross Btn
.select .v-text-field--full-width .v-input__prepend-inner,
.v-text-field--enclosed .v-input__append-inner {
  margin-top: 8px !important;
}
// Select Input
.v-application {
  font-family: "Source Sans Pro";
  line-height: 1.5;
}
.submit-container {
  margin: 25px;
  margin-left: 280px;
}
.submit-btn {
  width: 200px;
}
</style>