<template>
  <div class="menu-container">
    <v-menu offset-y :close-on-content-click="false" class="menu">
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" class="main-btn">
          Comp: {{ competitorTitle }}
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
            <v-radio class="radio" label="Custom" value="custom" />
          </v-radio-group>
        </v-list-item>
        <v-divider />
        <div class="custom-section ml-2 mr-2">
          <v-container>
            <div class="flex">
              <div>From</div>
              <v-text-field
                outlined
                :disabled="disabled"
                v-model="selectedItem"
                value="from"
              />
            </div>
          </v-container>
          <v-container>
            <div class="flex">
              <div>To*</div>
              <v-text-field
                outlined
                :disabled="disabled"
                value="to"
                v-model="selectedItem"
              />
            </div>
          </v-container>
        </div>
        <div class="section-label">*Max. value is unlimited</div>
        <div class="bottom">
          <v-btn class="apply-btn" :disabled="disabled"> Apply </v-btn>
        </div>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
export default {
  data: () => ({
    selectedItem: null,
    disabled: false,
    competitorTitle: "0-20",
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
    ],
  }),
};
</script>

<style>
</style>