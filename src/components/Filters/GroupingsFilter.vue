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
          Result Groupings
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list class="groupings-menu">
        <v-list-item>
          <div class="groupings-container">
            <v-select
              v-model="data.firstSelect"
              :items="groupingsEqualItems"
              :menu-props="{ bottom: true, offsetY: true }"
              class="selectBtn mt-2"
              filled
              outlined
            />
            <v-select
              v-model="data.secondSelect"
              :items="groupingsBestItems"
              :menu-props="{ bottom: true, offsetY: true }"
              class="selectBtn mt-2 ml-4"
              filled
              outlined
            />
          </div>
        </v-list-item>
        <v-list-item>
          <apply-btn 
            class="groupings-apply-btn"
            :title="'custom'"
            @close="$refs.menu.save()"
          />
        </v-list-item>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
import ApplyBtn from '../Shared/ApplyBtn.vue';
export default {
  props: ['data'],
  components: {
    ApplyBtn
  },
  data() {
    return {
      groupingsEqualSelect: "Equal to",
      groupingsEqualItems: ["Equal to", "Not equal to"],
      groupingsBestSelect: "All",
      groupingsBestItems: [
        "All",
        "Best Rankings/position (one URL per keyword)",
        "All URLs for all keywords",
        "Multiple Rankings",
      ],
    };
  },
};
</script>

<style>
.groupings-container {
  display: flex;
}
.apply-btn.groupings-apply-btn {
  width: 336px;
  margin-top: 24px;
  margin-bottom: 12px;
}
</style>