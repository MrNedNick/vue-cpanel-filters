<template>
  <div class="wrapper">
    <div class="top-section">
      <internet-field />
      <v-btn
        class="filter-btn ml-4"
        elevation="0"
        height="40"
        @click="showFilters()"
      >
        <v-icon color="#3366FF">mdi-filter-variant</v-icon>
        Filter
      </v-btn>
    </div>
    <div v-if="true" class="filter-section">
      <div v-if="isShown" class="filter-section">
        <div class="filter-wrapper">
          <position-filter :data="position" @updateData="updatePosition" />
          <volume-filter :data="volume" />
          <cpc-filter :data="cpc" />
          <competitor-filter :data="competitor" />
          <advanced-filter />
          <groupings-filter :data="groupings" />
          <word-count-filter :data="word" @updateData="updateWord" />
        </div>
        <div class="btns-wrapper">
          <v-btn class="apply-btn" width="83" height="40"> Apply </v-btn>
          <v-btn
            class="clear-btn ml-4"
            color="#3366FF"
            outlined
            width="98"
            height="40"
            @click="clearFilters()"
          >
            Clear All
          </v-btn>
          <v-btn class="save-all-btn ml-4" href="#" elevation="0" height="40">
            <v-icon color="#3366FF" class="advanced-btn_icon">mdi-plus</v-icon>
            Save Filter
          </v-btn>
        </div>
        <data-table
          :position="position"
          :volume="volume"
          :cpc="cpc"
          :competitor="competitor"
          :groupings="groupings"
          :advanced="conditions"
          :word="word"
        />
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
import DataTable from "./Shared/DataTable.vue";
import InternetField from "./Shared/InternetField.vue";
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
    InternetField,
    DataTable,
  },
  data() {
    return {
      isShown: false,
      position: {
        title: "",
        from: "0",
        to: "",
      },
      volume: {
        title: "",
        from: "0",
        to: "",
      },
      cpc: {
        title: "",
        from: "0",
        to: "",
      },
      competitor: {
        title: "",
        from: "0",
        to: "",
      },
      conditions: [{ id: 1 }],
      advanced: [
        {
          id: 1,
          advancedSelect: "",
          advancedKeywordSelect: "",
          advancedPathSelect: "",
          advancedTextField: "",
        },
      ],
      groupings: {
        firstSelect: "",
        secondSelect: "",
      },
      word: [],
      wordRange: { from: "", to: "" },
    };
  },
  methods: {
    showFilters() {
      this.isShown = !this.isShown;
    },
    deleteCondition(id) {
      this.conditions = this.conditions.filter((task) => task.id !== id);
    },
    updatePosition(newData) {
      this.position.title = newData;
    },
    updateWord(newData) {
      this.word = newData;
    },
    clearFilters() {
      this.position.title = "";
      this.position.from = "";
      this.position.to = "";

      this.volume.title = "";
      this.volume.from = "";
      this.volume.to = "";

      this.cpc.title = "";
      this.cpc.from = "";
      this.cpc.to = "";

      this.competitor.title = "";
      this.competitor.from = "";
      this.competitor.to = "";

      this.advanced = [];

      this.groupings.firstSelect = "";
      this.groupings.secondSelect = "";

      this.word = [];
    },
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
  width: 1328px;
  min-height: 300px;
  margin-top: 100px;
}
.filter-wrapper {
  display: flex;
  // flex-wrap: wrap;
}
.top-section {
  display: flex;
}
.menu-container {
  margin-top: 40px;
}
.advanced-container {
  display: flex;
  height: 40px !important;
}

.main-btn.v-btn:not(.v-btn--round).v-size--default {
  width: 160px;
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
// internet-field
.internet-field.v-text-field--outlined > .v-input__control > .v-input__slot {
  min-height: 0px !important;
  max-width: 448px !important;
  height: 40px;
  border-radius: 6px;
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
.submit-btn {
  width: 200px;
}
// Save Btn
// .save-btn {
//   & .v-btn__content {
//     font-family: "Source Sans Pro";
//     font-weight: 400;
//     font-size: 14px;
//     color: #3366ff;
//     text-transform: none;
//     letter-spacing: 0em;
//   }
// }
.filter-btn {
  font-family: "Source Sans Pro";
  font-weight: 600;
  font-size: 14px;
  line-height: 18px;
  text-transform: none;
  letter-spacing: 0em;
  color: #3366ff !important;
  opacity: 0.8;
}
.save-all-btn {
  font-family: "Source Sans Pro";
  font-weight: 600;
  font-size: 14px;
  line-height: 18px;
  text-transform: none;
  letter-spacing: 0em;
  color: #05122d;
  opacity: 0.8;
}
.clear-btn {
  font-family: "Source Sans Pro", sans-serif;
  font-weight: 600;
  font-size: 14px;
  line-height: 18px;
  text-transform: capitalize;
}
.table {
  display: flex;
  flex-direction: column;
}
</style>