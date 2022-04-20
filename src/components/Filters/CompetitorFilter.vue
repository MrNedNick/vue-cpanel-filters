<template>
  <div class="menu-container ml-6">
    <v-menu :close-on-content-click="false" class="menu" ref="menu" offset-y>
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" class="main-btn">
          Comp:
          {{
            data.title !== "custom" ? data.title : `${data.from} - ${data.to}`
          }}
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list class="menu">
        <radio-select
          :items="competitorRadioBtns"
          :title="data.title"
          @update-title="update"
        />
        <custom-section :title="data.title" :range="data" />
        <div class="bottom">
          <apply-btn :title="data.title" @close="$refs.menu.save()" />
        </div>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
import ApplyBtn from "../Shared/ApplyBtn.vue";
import CustomSection from "../Shared/CustomSection.vue";
import RadioSelect from "../Shared/RadioSelect.vue";
export default {
  props: ["data"],
  components: { ApplyBtn, CustomSection, RadioSelect },
  methods: {
    update(title) {
      this.data.title = title;
    },
  },
  data() {
    return {
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
    };
  },
};
</script>

<style>
</style>