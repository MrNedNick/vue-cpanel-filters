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
          <v-select
            class="select"
            :items="items"
            clearable
            offset-y
            outlined
            append-icon="mdi-chevron-down"
            color="#033"
            background-color="white"
            deletable-chips
            :menu-props="{ top: false, offsetY: true, maxHeight: 700 }"
          >
            <template v-slot:prepend-inner class="input-title">
              Volume:
            </template>
            <template v-slot:append-item>
              <v-radio-group v-model="volumeTitle">
                <v-radio
                  class="radio"
                  v-for="btn in volumeRadioBtns"
                  :key="btn.id"
                  :label="btn.label"
                  :value="btn.value"
                />
                <v-radio class="radio" label="Custom" value="custom" />
              </v-radio-group>
              <v-divider />
              <div class="custom-section ml-2 mr-2">
                <v-container>
                  <div class="flex">
                    <div>From</div>
                    <v-text-field outlined value="from" />
                  </div>
                </v-container>
                <v-container>
                  <div class="flex">
                    <div>To*</div>
                    <v-text-field outlined value="to" />
                  </div>
                </v-container>
              </div>
              <div class="section-label">*Max. value is unlimited</div>
              <div class="bottom">
                <v-btn class="apply-btn"> Apply </v-btn>
              </div>
            </template>
          </v-select>
        </div>

        <!-- <v-btn
          :disabled="!valid"
          color="success"
          class="mr-4"
          @click="validate"
        >
          Validate
        </v-btn> -->


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
    menuProps: {
      closeOnClick: false,
      closeOnContentClick: false,
      disableKeys: true,
      openOnClick: false,
      maxHeight: 700,
    },
    disabled: false,
    volumeTitle: "0-10",
    volumeRange: [{ from: "0" }, { to: "0" }],
    volumeRadioBtns: [
      {
        id: 1,
        label: "0-10",
        value: "0-10",
      },
      {
        id: 2,
        label: "11-100",
        value: "11-100",
      },
      {
        id: 3,
        label: "101-1000",
        value: "101-1000",
      },
      {
        id: 4,
        label: "1001-5000",
        value: "1001-5000",
      },
    ],
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
.v-list-item {
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
  border-radius: 6px;
}
// apply btn
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
</style>