<template>
  <div class="menu-container ml-6">
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
  props: ["data"],
  components: { ApplyBtn, CustomSection },
  methods: {
    isDisabled() {
      return this.value.includes("custom") ? "custom" : "";
    },
  },
  data() {
    return {
      value: this.data,
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
      wordRange: { from: "", to: "" },
    };
  },
  computed: {
    newData() {
      return this.value;
    },
  },
  watch: {
    newData(newValue, oldValue) {
      console.log('up')
      this.$emit("updateData", this.value);
    },
  },
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
  width: 200px;
}
.v-select .v-chip {
  margin: 0px;
}
.select.v-text-field--filled > .v-input__control > .v-input__slot,
.v-text-field--full-width > .v-input__control > .v-input__slot,
.v-text-field--outlined > .v-input__control > .v-input__slot {
  max-width: 210px !important;
}
</style>