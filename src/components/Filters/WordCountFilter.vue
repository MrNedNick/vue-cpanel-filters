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
    <v-select
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
      <template v-slot:prepend-inner class="input-title"> 
        Word count
      </template>
      <template v-slot:selection="{ index }">
        <v-chip v-if="index === 0">
          <span>{{ value.length }}</span>
        </v-chip>
      </template>
      <template v-slot:append-item>
        <!-- <custom-section></custom-section>
        <apply-btn></apply-btn> -->
      </template>
    </v-select>

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
  </div>
</template>

<script>
import ApplyBtn from "../Shared/ApplyBtn.vue";
import CustomSection from "../Shared/CustomSection.vue";
export default {
  components: { ApplyBtn, CustomSection },
  data: () => ({
    items: ["1", "2", "3", "4-10", "Custom"],
    value: [],
    selectedItem: null,
    disabled: false,
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
.v-input__prepend-inner{
  width: 145px;
}
</style>