<template>
  <div>
    <v-divider />
    <div class="custom-section ml-2 mr-2">
      <v-container>
        <div class="flex">
          <div>From</div>
          <v-text-field
            outlined
            :disabled="isDisabled()"
            v-model="range.from"
            placeholder="0"
          />
        </div>
      </v-container>
      <div class="custom-line">-</div>
      <v-container>
        <div class="flex">
          <div>To*</div>
          <v-text-field
            outlined
            :disabled="isDisabled()"
            v-model="range.to"
            placeholder="0"
          />
        </div>
      </v-container>
    </div>
    <div class="section-label mb-4">*Max. value is unlimited</div>
    <v-divider />
  </div>
</template>

<script>
export default {
  props: [
    'title',
    'range'
  ],
  methods: {
    isDisabled() {
      return this.title !== "custom";
    },
  },
};
</script>

<style>
.custom-section{
  height: 120px;
}
</style>