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
      <a href="#" class="clear-btn ml-4" @click="clearAll"> Clear all </a>
      <a href="#" class="delete-btn" @click="$emit('delete')">
        <v-icon small>mdi-close</v-icon>
      </a>
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
.clear-btn {
  font-family: "Source Sans Pro";
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 166%;
  color: #3366ff; 
  text-decoration: none;
  transition: all 0.1s linear;
  border-right: 1px solid rgba(51, 51, 51, 0.2);
}
.clear-btn:hover {
  color: #0040ff;
}
.clear-btn:active {
  color: black;
}
</style>