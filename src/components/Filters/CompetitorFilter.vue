<template>
  <div class="menu-container ml-6">
    <v-menu
      :close-on-content-click="false"
      class="menu"
      ref="menu"
      offset-y
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" class="main-btn">
          Comp:
          {{
            competitorTitle !== "custom"
              ? competitorTitle
              : `${competitorRange.from} - ${competitorRange.to}`
          }}
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list class="menu">
        <v-list-item>
          <v-radio-group v-model="competitorTitle">
            <v-radio
              class="radio"
              v-for="btn in competitorRadioBtns"
              :key="btn.id"
              :label="btn.label"
              :value="btn.value"
            />
          </v-radio-group>
        </v-list-item>
        <custom-section
          :range="competitorRange"
          :title="competitorTitle"
        />
        <div class="bottom">
          <apply-btn 
            :title="this.competitorTitle"
            @close="$refs.menu.save()"
          />
        </div>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
import ApplyBtn from '../Shared/ApplyBtn.vue';
import CustomSection from '../Shared/CustomSection.vue';
export default {
  components: { ApplyBtn, CustomSection },
  data: () => ({
    competitorTitle: "",
    competitorRange: { from: "", to: "" },
    competitorRadioBtns: [
      {
        id: 1,
        label: "0-20",
        value: "0-20",
      },
      {
        id: 2,
        label: "21-50",
        value: "21-50",
      },
      {
        id: 3,
        label: "51-75",
        value: "51-75",
      },
      {
        id: 4,
        label: "76-100",
        value: "76-100",
      },
      {
        id: 5,
        label: "Custom",
        value: "custom",
      },
    ],
  }),
};
</script>

<style>
</style>