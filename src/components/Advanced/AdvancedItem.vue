<template>
  <v-list-item>
    <div class="advanced-container">
      <v-select
        v-model="advancedSelect"
        :items="advancedSelectItems"
        :menu-props="{
          bottom: true,
          offsetY: true,
          maxWidth: 160,
        }"
        class="selectBtn"
        filled
        outlined
      >
      </v-select>
      <v-select
        v-if="advancedSelect === 'Keyword' || advancedSelect === ''"
        v-model="advancedKeywordSelect"
        :items="advancedKeywordItems"
        :menu-props="{ bottom: true, offsetY: true, maxWidth: 160 }"
        class="selectBtn ml-3"
        filled
        outlined
      ></v-select>
      <v-select
        v-if="advancedSelect === 'Path'"
        v-model="advancedPathSelect"
        :items="advancedPathItems"
        :menu-props="{ bottom: true, offsetY: true }"
        class="selectBtn ml-3"
        filled
        outlined
      ></v-select>
      <v-text-field
        v-model="advancedTextField"
        class="advanced-field ml-3"
        filled
        outlined
        placeholder="Write here..."
      ></v-text-field>
      <v-btn class="advanced-btn clear" elevation="0" @click="clearAll">
        Clear all
      </v-btn>
      <v-icon small>mdi-close</v-icon>
    </div>
  </v-list-item>
</template>

<script>
export default {
  methods: {
    clearAll() {
      this.advancedSelect = "";
      this.advancedKeywordSelect = "";
      this.advancedPathSelect = "";
      this.advancedTextField = "";
    },
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
    advancedTextField: "",
  }),
};
</script>

<style>
</style>