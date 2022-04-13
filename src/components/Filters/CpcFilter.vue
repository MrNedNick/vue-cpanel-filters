<template>
  <div class="menu-container">
    <v-menu offset-y :close-on-content-click="false" class="menu">
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" class="main-btn">
          CPC:
          {{
            cpcTitle !== "custom"
              ? cpcTitle
              : `${cpcRange.from} - ${cpcRange.to}`
          }}
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list class="menu">
        <v-list-item>
          <v-radio-group v-model="cpcTitle">
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
                class="custom-textfield"
                v-model="cpcRange.from"
                :disabled="isDisabled()"
                append-icon="mdi-currency-eur"
                value="from"
                outlined
                placeholder="0"
              />
            </div>
          </v-container>
          <div class="custom-line">-</div>
          <v-container>
            <div class="flex">
              <div>To*</div>
              <v-text-field
                class="custom-textfield"
                v-model="cpcRange.to"
                :disabled="isDisabled()"
                outlined
                append-icon="mdi-currency-eur"
                placeholder="0"
              />
            </div>
          </v-container>
        </div>
        <div class="section-label">*Max. value is unlimited</div>
        <div class="bottom">
          <v-btn class="apply-btn" :disabled="isDisabled()"> Apply </v-btn>
        </div>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
export default {
  methods: {
    isDisabled() {
      return this.cpcTitle !== "custom";
    },
  },
  data: () => ({
    cpcTitle: "",
    cpcRange: { from: "", to: "" },
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
      {
        id: 4,
        label: "Custom",
        value: "custom",
      },
    ],
  }),
};
</script>

<style>
/* € */
.custom-textfield .v-icon.v-icon {
  font-size: 14px;
}
.custom-section .v-text-field--enclosed .v-input__append-inner {
  margin-top: 4px !important;
}
</style>