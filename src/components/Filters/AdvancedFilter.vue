<template>
  <div class="menu-container">
    <v-menu :close-on-content-click="false" class="menu" offset-y>
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" class="main-btn">
          Advanced Filters
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list class="advanced-menu">
        <advanced-item />
        <advanced-item />
        <v-list-item>
          <v-btn class="advanced-btn add" elevation="0" @click="addCondition">
            <v-icon color="primary">mdi-plus</v-icon>
            Add Condition
          </v-btn>
        </v-list-item>
        <v-list-item>
          <v-btn class="apply-btn advanced-apply-btn mt-5 mb-3"> Apply </v-btn>
        </v-list-item>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
import AdvancedItem from "../Advanced/AdvancedItem.vue";
export default {
  components: { AdvancedItem },
  methods: {
    addCondition() {},
  },
  data: () => ({
    advancedSelect: "Keyword",
    advancedSelectItems: ["Keyword", "Path"],
    advancedKeywordSelect: "Contains",
    advancedKeywordItems: [
      "Contains",
      "Does not contain",
      "Equal to",
      "Not equal to",
      "Starts with",
      "Does not start with",
    ],
    advancedPathSelect: "Starts with",
    advancedPathItems: ["Starts with", "Does not start with"],
    selectedItem: null,
    disabled: false,
  }),
};
</script>

<style lang='scss'>
.advanced-menu {
  width: 648px;
  display: flex;
}
.advanced-container {
  display: flex;
  align-items: baseline;
}
.selectBtn {
  width: 160px;
  max-height: 40px;
}
.v-text-field--filled > .v-input__control > .v-input__slot,
.v-text-field--full-width > .v-input__control > .v-input__slot,
.v-text-field--outlined > .v-input__control > .v-input__slot {
  min-height: 0px !important;
  max-width: 140px !important;
  max-height: 40px !important;
  border-radius: 6px;
}
.v-text-field--full-width .v-input__prepend-outer,
.v-text-field--full-width .v-input__prepend-inner,
.v-text-field--full-width .v-input__append-inner,
.v-text-field--full-width .v-input__append-outer,
.v-text-field--enclosed .v-input__prepend-outer,
.v-text-field--enclosed .v-input__prepend-inner,
.v-text-field--enclosed .v-input__append-inner,
.v-text-field--enclosed .v-input__append-outer {
  margin-top: 4px !important;
}
.main-btn {
  width: 160px;
  height: 40px;
  border: 1px solid rgba(26, 44, 89, 0.4);
  & .v-btn__content {
    font-family: "Source Sans Pro";
    font-weight: 400;
    font-size: 16px;
    line-height: 166%;
    letter-spacing: 0em;
    color: #05122d;
    text-transform: none;
    display: flex;
    justify-content: space-between;
  }
  &.v-btn--is-elevated {
    box-shadow: none !important;
  }
  &.v-btn:not(.v-btn--round).v-size--default {
    padding: 0 8px 0 !important;
    width: 160px;
    height: 40px;
    background: rgba(26, 44, 89, 0.04);
  }
}
.advanced-apply-btn {
  width: 616px !important;
}
.advanced-btn {
  & .v-btn__content {
    font-family: "Source Sans Pro";
    font-weight: 400;
    font-size: 14px;
    color: #3366ff;
    text-transform: none;
    letter-spacing: 0em;
  }
}
.advanced-btn.add {
  & .v-btn__content {
    font-family: "Source Sans Pro";
    font-weight: 600;
    font-size: 14px;
    line-height: 18px;
    color: #05122d;
  }
}
.advanced-btn.theme--light.v-btn.v-btn--has-bg {
  background-color: white !important;
}
.advanced-field {
  width: 160px;
}
</style>