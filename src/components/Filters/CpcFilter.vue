<template>
  <div class="menu-container ml-6">
    <v-menu :close-on-content-click="false" class="menu" ref="menu" offset-y>
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" class="main-btn">
          CPC:
          {{
            data.title !== "custom" ? data.title : `${data.from} - ${data.to}`
          }}
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list class="menu">
        <radio-select
          :items="cpcRadioBtns"
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
    };
  },
  // computed: {
  //   changeTitle() {
  //     return this.cpcTitle
  //   },
  // },
  // watch: {
  //   changeTitle(newValue, oldValue) {
  //     this.$emit("updateParent", this.cpcTitle);
  //   },
  // },
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