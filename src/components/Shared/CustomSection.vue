<template>
  <div>
    <v-divider />
    <div class="custom-section ml-2 mr-2">
      <v-container>
        <div class="flex">
          <div>From</div>
          <v-text-field
            outlined
            :disabled="$emit('isDisabled')"
            v-model="range.to"
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
            :disabled="$emit('isDisabled')"
            v-model="range.to"
            placeholder="0"
          />
        </div>
      </v-container>
    </div>
    <div class="section-label">*Max. value is unlimited</div>
    <div class="bottom">
      <v-btn class="apply-btn" :disabled="$emit('isDisabled')"> Apply </v-btn>
    </div>
  </div>
</template>

<script>
export default {
  props: [],
  // methods: {
  //   isDisabled() {
  //     return this.title !== "custom";
  //   },
  // },
};
</script>

<style>
</style>