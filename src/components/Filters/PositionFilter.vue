<template>
  <div class="menu-container">
    <v-menu
      :close-on-content-click="false"
      class="menu"
      ref="menu"
      offset-y
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" class="main-btn">
          Pos:
          {{
            positionTitle !== "custom"
              ? positionTitle
              : `${positionRange.from} - ${positionRange.to}`
          }}
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list class="menu">
        <radio-select
          :items="positionRadioBtnsTop"
          :title="positionTitle"
          @update-title="update"
        />
        <v-divider />
        <radio-select
          :items="positionRadioBtns"
          :title="positionTitle"
          @update-title="update"
        />
        <custom-section
          :range="positionRange"
          :title="positionTitle"
        />
        <apply-btn 
          :title="positionTitle" 
          @close="$refs.menu.save()"
        />
      </v-list>
    </v-menu>
  </div>
</template>

<script>
import ApplyBtn from "../Shared/ApplyBtn.vue";
import CustomSection from "../Shared/CustomSection.vue";
import RadioSelect from "../Shared/RadioSelect.vue";
export default {
  components: { ApplyBtn, CustomSection, RadioSelect },
  methods: {
    update(title) {
      this.positionTitle = title;
    },
  },
  data: () => ({
    positionTitle: "",
    positionRange: { from: "", to: "" },
    positionRadioBtnsTop: [
      {
        id: 1,
        label: "Top 50",
        value: "Top 50",
      },
      {
        id: 2,
        label: "Top 20",
        value: "Top 20",
      },
      {
        id: 3,
        label: "Top 10",
        value: "Top 10",
      },
      {
        id: 4,
        label: "Top 3",
        value: "Top 3",
      },
    ],
    positionRadioBtns: [
      {
        id: 5,
        label: "1",
        value: "1",
      },
      {
        id: 6,
        label: "4-10",
        value: "4-10",
      },
      {
        id: 7,
        label: "11-20",
        value: "11-20",
      },
      {
        id: 8,
        label: "21-50",
        value: "21-50",
      },
      {
        id: 9,
        label: "51-100",
        value: "51-100",
      },
      {
        id: 10,
        label: "Custom",
        value: "custom",
      },
    ],
  }),
};
</script>

<style>
</style>