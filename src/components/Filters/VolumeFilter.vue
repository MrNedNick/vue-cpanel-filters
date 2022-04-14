<template>
  <div class="menu-container">
    <v-menu :close-on-content-click="false" class="menu" offset-y>
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" class="main-btn">
          Volume:
          {{
            volumeTitle !== "custom"
              ? volumeTitle
              : `${volumeRange.from} - ${volumeRange.to}`
          }}
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list class="menu">
        <v-list-item>
          <v-radio-group v-model="volumeTitle">
            <v-radio
              class="radio"
              v-for="btn in volumeRadioBtns"
              :key="btn.id"
              :label="btn.label"
              :value="btn.value"
            />
          </v-radio-group>
        </v-list-item>
        <!-- <radio-select
        ></radio-select> -->
        <!-- <custom-section
          @isDisabled="isDisabled"
        /> -->
        <!-- <v-divider />
        <div class="custom-section ml-2 mr-2">
          <v-container>
            <div class="flex">
              <div>From</div>
              <v-text-field
                outlined
                :disabled="isDisabled()"
                v-model="volumeRange.from"
                placeholder="0"
              />
            </div>
          </v-container>
          <div class="custom-line">-</div>
          <v-container>
            <div class="flex">
              <div>To*</div>
              <v-text-field
                outlined
                :disabled="isDisabled()"
                v-model="volumeRange.to"
                placeholder="0"
              />
            </div>
          </v-container>
        </div>
        <div class="section-label">*Max. value is unlimited</div> -->
        <!-- <div class="bottom">
          <v-btn class="apply-btn" :disabled="isDisabled()"> Apply </v-btn>
        </div> -->
        <apply-btn 
          :title="volumeTitle"
        ></apply-btn>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
import RadioSelect from "../Shared/RadioSelect.vue";
import CustomSection from "../Shared/CustomSection.vue";
import ApplyBtn from '../Shared/ApplyBtn.vue';
export default {
  components: {
    RadioSelect,
    CustomSection,
    ApplyBtn,
  },
  data() {
    return {
      volumeTitle: "",
      volumeRange: { from: "", to: "" },
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
        {
          id: 5,
          label: "Custom",
          value: "custom",
        },
      ],
    };
  },
  methods: {
    isDisabled() {
      return this.volumeTitle !== "custom";
    },
    closeMenu() {
      console.log("close");
    },
  },
};
</script>

<style>
/* .v-list-item {
  padding: 0;
}
.radio {
  margin-top: 0px;
  padding: 8px 50px 8px 8px;
  width: 201px;
}
.radio:hover {
  background-color: rgb(235, 235, 235);
}
.v-input--radio-group--column .v-radio:not(:last-child):not(:only-child) {
  margin-bottom: 0px;
} */

/* menuable__content__active */
</style>