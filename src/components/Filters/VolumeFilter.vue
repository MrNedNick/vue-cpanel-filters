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
          Volume:
          {{
            volumeTitle !== "custom"
              ? volumeTitle
              : `${volumeRange.from} - ${volumeRange.to}`
          }}
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list class="menu">
        <v-list-item>
          <v-radio-group v-model="volumeTitle">
            <v-radio
              class="radio"
              v-for="btn in volumeRadioBtns"
              :key="btn.id"
              :label="btn.label"
              :value="btn.value"
            />
          </v-radio-group>
        </v-list-item>
        <!-- <radio-select
        ></radio-select> -->
        <custom-section
          :title="volumeTitle"
          :range="volumeRange"
        />  
        <div class="bottom">
          <apply-btn 
            :title="volumeTitle"
            @close="$refs.menu.save()"
          />
        </div>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
import RadioSelect from "../Shared/RadioSelect.vue";
import CustomSection from "../Shared/CustomSection.vue";
import ApplyBtn from '../Shared/ApplyBtn.vue';
export default {
  components: {
    RadioSelect,
    CustomSection,
    ApplyBtn,
  },
  data() {
    return {
      volumeTitle: "",
      volumeRange: { from: "", to: "" },
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
        {
          id: 5,
          label: "Custom",
          value: "custom",
        },
      ],
    };
  },
  methods: {
    changeTitle() {
      console.log(this.volumeTitle)
    }
  },
  computed: {
    salary() {
      return this.volumeTitle
    }
  },

  watch: {
    // Эта функция запускается при любом изменении значений
    // в вычисляемом свойстве `salary`.
    salary(newValue, oldValue) {
      // Пробрасываем данные родительскому компоненту,
      // ч/з вызов метода.
      this.$emit('updateParent', 
        this.volumeTitle
      )
    }
  }
};
</script>
