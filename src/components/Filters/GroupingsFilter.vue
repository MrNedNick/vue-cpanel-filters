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
          Result Groupings
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list class="groupings-menu">
        <v-list-item>
          <div class="groupings-container">
            <v-select
              v-model="groupingsEqualSelect"
              :items="groupingsEqualItems"
              :menu-props="{ bottom: true, offsetY: true }"
              class="selectBtn mt-2"
              filled
              outlined
            />
            <v-select
              v-model="groupingsBestSelect"
              :items="groupingsBestItems"
              :menu-props="{ bottom: true, offsetY: true }"
              class="selectBtn mt-2 ml-4"
              filled
              outlined
            />
          </div>
        </v-list-item>
        <v-list-item>
          <v-btn class="apply-btn groupings-apply-btn"> Apply </v-btn>
        </v-list-item>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
export default {
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