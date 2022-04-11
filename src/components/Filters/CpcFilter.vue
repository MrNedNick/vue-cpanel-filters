<template>
  <div class="menu-container">
    <v-menu offset-y :close-on-content-click="false" class="menu">
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" class="main-btn">
          CPC: {{ cpc }}
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list class="menu">
        <v-list-item>
          <v-radio-group v-model="cpc">
            <v-radio
              class="radio"
              v-for="btn in cpcRadioBtns"
              :key="btn.id"
              :label="btn.label"
              :value="btn.value"
            />
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
                v-model="cpcFrom"
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
                v-model="cpcTo"
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
    disabled: false,
    cpc: "0-0.50 €",
    cpcFrom: "0",
    cpcTo: "",
    cpcRadioBtns: [
      {
        id: 1,
        label: "0-0.50 €",
        value: "0-0.50 €",
      },
      {
        id: 2,
        label: "0.51-2.00 €",
        value: "0.51-2.00 €",
      },
      {
        id: 3,
        label: "2.01-5.00 €",
        value: "2.01-5.00 €",
      },
    ],
  }),
};
</script>

<style>
</style>