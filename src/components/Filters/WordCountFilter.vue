<template>
  <div class="menu-container">
    <!-- <v-menu
      :close-on-content-click="false"
      class="menu"
      ref="menu"
      offset-y
    > -->
    <!-- <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" class="main-btn">
          Word Count
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list class="menu">
        <v-list-item> -->
    <!-- <div class="checkbox-container">
            <v-checkbox class="pt-3 radio" label="1" />
            <v-checkbox class="checkbox radio" label="2" />
            <v-checkbox class="checkbox radio" label="3" />
            <v-checkbox class="checkbox radio" label="4-10" />
            <v-checkbox class="checkbox radio" label="Custom" />
          </div> -->
    <!-- </v-list-item>
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
          <div class="custom-line">-</div>
          <v-container>
            <div class="flex">
              <div>To*</div>
              <v-text-field
                outlined
                :disabled="disabled"
                v-model="selectedItem"
                value="to"
              />
            </div>
          </v-container>
        </div>
        <div class="section-label">*Max. value is unlimited</div>
        <div class="bottom">
          <v-btn class="apply-btn" :disabled="disabled"> Apply </v-btn>
        </div> -->
    <!-- </v-list>
    </v-menu> -->
    <v-select
      ref="select"
      v-model="value"
      :items="items"
      multiple
      class="select"
      clearable
      offset-y
      outlined
      append-icon="mdi-chevron-down"
      color="#033"
      background-color="white"
      deletable-chips
      :menu-props="{
        top: false,
        offsetY: true,
        maxHeight: 700,
        maxWidth: 200,
      }"
    >
      <template v-slot:prepend-inner class="input-title"> Word count </template>
      <template v-slot:selection="{ index }">
        <v-chip v-if="index === 0">
          <span>{{ value.length }}</span>
        </v-chip>
      </template>
      <template v-slot:append-item>
        <custom-section :range="wordRange" :title="isDisabled()" />
        <apply-btn
          :title="isDisabled()"
          @close="$refs.select.blur()"
          class="ma-4"
        />
      </template>
    </v-select>
  </div>
</template>

<script>
import ApplyBtn from "../Shared/ApplyBtn.vue";
import CustomSection from "../Shared/CustomSection.vue";
export default {
  components: { ApplyBtn, CustomSection },
  methods: {
    isDisabled() {
      return this.value.includes("custom") ? "custom" : "";
    },
  },
  data: () => ({
    items: [
      {
        text: "1",
        value: "1",
      },
      {
        text: "2",
        value: "2",
      },
      {
        text: "3",
        value: "3",
      },
      {
        text: "4-10",
        value: "4-10",
      },
      {
        text: "Custom",
        value: "custom",
      },
    ],
    value: [],
    wordRange: { from: "", to: "" },
  }),
};
</script>

<style>
.checkbox-container {
  display: flex;
  flex-direction: column;
}
.checkbox {
  display: flex;
  justify-content: center;
  align-items: center;
}
.v-input__prepend-inner {
  width: 147px;
}
</style>