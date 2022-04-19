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
        <custom-section
          :range="cpcRange"
          :title="cpcTitle"
        />
        <div class="bottom">
          <apply-btn 
            :title="this.cpcTitle"
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