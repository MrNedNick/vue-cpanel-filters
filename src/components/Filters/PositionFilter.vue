<template>
  <div class="menu-container">
    <v-menu offset-y :close-on-content-click="false" class="menu">
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" class="main-btn">
          Pos: {{ positionTitle }}
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list class="menu">
        <v-list-item>
          <v-radio-group v-model="positionTitle">
            <v-radio
              class="radio"
              v-for="btn in positionRadioBtnsTop"
              :key="btn.id"
              :label="btn.label"
              :value="btn.value"
            />
          </v-radio-group>
        </v-list-item>
        <v-divider />
        <v-list-item>
          <v-radio-group v-model="positionTitle">
            <v-radio
              class="radio"
              v-for="btn in positionRadioBtns"
              :key="btn.id"
              :label="btn.label"
              :value="btn.value"
            />
            <v-radio class="radio" label="Custom" value="custom" />
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
                v-model="volumeRange.from"
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
                value="to"
                v-model="volumeRange.to"
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

    positionTitle: "Top 50",
    positionRadioBtnsTop: [
      {
        id: 1,
        label: "Top 50",
        value: "Top 50",
      },
      {
        id: 2,
        label: "Top 20",
        value: "Top 20",
      },
      {
        id: 3,
        label: "Top 10",
        value: "Top 10",
      },
      {
        id: 4,
        label: "Top 3",
        value: "Top 3",
      },
    ],
    positionRadioBtns: [
      {
        id: 5,
        label: "1",
        value: "1",
      },
      {
        id: 6,
        label: "4-10",
        value: "4-10",
      },
      {
        id: 7,
        label: "11-20",
        value: "11-20",
      },
      {
        id: 8,
        label: "21-50",
        value: "21-50",
      },
      {
        id: 9,
        label: "51-100",
        value: "51-100",
      },
    ],
    volumeRange: [{ from: "0" }, { to: "0" }],
  }),
};
</script>

<style>
</style>