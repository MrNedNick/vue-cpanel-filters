<template>
  <v-app id="inspire">
    <div class="wrapper">
      <div class="container">
        <advanced-filter />
        <position-filter>djfdlsfj</position-filter>
        <volume-filter />
        <cpc-filter />
        <word-count-filter />
        <groupings-filter />
        <competitor-filter />

        <div class="menu-container">
          <v-select outlined :items="items" offset-y> </v-select>
          <slot>fsalkjfls</slot>
        </div>
      </div>
    </div>
  </v-app>
</template>

<script>
import AdvancedFilter from "./components/Filters/AdvancedFilter.vue";
import CompetitorFilter from "./components/Filters/CompetitorFilter.vue";
import CpcFilter from "./components/Filters/CpcFilter.vue";
import GroupingsFilter from "./components/Filters/GroupingsFilter.vue";
import PositionFilter from "./components/Filters/PositionFilter.vue";
import VolumeFilter from "./components/Filters/VolumeFilter.vue";
import WordCountFilter from "./components/Filters/WordCountFilter.vue";
export default {
  components: {
    AdvancedFilter,
    GroupingsFilter,
    PositionFilter,
    VolumeFilter,
    CpcFilter,
    WordCountFilter,
    CompetitorFilter,
  },
  data: () => ({
    items: ["Foo", "Bar", "Fizz", "Buzz"],
  }),
  methods: {},
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
  background-color: #f5f6f7;
  min-height: 1500px;
}
.container {
  display: flex;
  flex-wrap: wrap;
}
.menu-container {
  margin-left: 40px;
  margin-top: 100px;
}
.advanced-container {
  display: flex;
  height: 40px !important;
}
.menu {
  max-width: 201px;
  margin-top: -24px;
}
.radio {
  margin-top: 8px;
}
.theme--light.v-label {
  color: #05122d !important;
}
.custom-section {
  display: flex;
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
  max-width: 160px !important;
  border-radius: 6px;
}
.apply-btn {
  width: 169px;
  height: 40px;

  & .v-btn__content {
    color: white;
    font-family: Source Sans Pro;
    font-weight: 600;
    font-size: 14px;
    line-height: 18px;
    text-transform: none;
  }
}
// apply btn
.apply-btn.theme--light.v-btn.v-btn--has-bg {
  background-color: #3366ff !important;
  border-radius: 6px;
}
.apply-btn.theme--light.v-btn.v-btn--disabled.v-btn--has-bg {
  background-color: rgba(0, 0, 0, 0.12) !important;
}

.bottom {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 36px;
  margin-bottom: 16px;
}
</style>