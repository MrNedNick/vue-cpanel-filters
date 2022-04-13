<template>
  <v-list-item>
    <v-radio-group v-model="volumeTitle">
      <v-radio
        class="radio"
        v-for="radio in volumeRadioBtns"
        :key="radio.id"
        :label="radio.label"
        :value="radio.value"
      />
      <!-- <v-radio class="radio" label="Custom" value="custom" /> -->
    </v-radio-group>
  </v-list-item>
</template>

<script>
export default {
  props: [""],
  data() {
    return {
      disabled: false,
      volumeTitle: "0-10",
      volumeRange: [{ from: "0" }, { to: "0" }],
      volumeRadioBtns: [
        {
          id: 1,
          label: "0-10",
          value: "0-10",
        },
        {
          id: 2,
          label: "11-100",
          value: "11-100",
        },
        {
          id: 3,
          label: "101-1000",
          value: "101-1000",
        },
        {
          id: 4,
          label: "1001-5000",
          value: "1001-5000",
        },
      ],
    };
  },
  methods: {
    isDisabled() {
      return this.volumeTitle !== "custom" 

    },
  },
};
</script>

<style>
</style>