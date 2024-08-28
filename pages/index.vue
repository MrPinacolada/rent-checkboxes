<template>
  <header>Total percent: {{ percentChecked }}%</header>
  <main class="checkboxes__container">
    <div class="checkbox" v-for="item in checkboxArr" :key="item.label">
      <input
        type="checkbox"
        style="height: 20px; width: 20px"
        v-model="item.value"
        @change="calcPercent"
      />
      <p>{{ item.label }}</p>
    </div>
  </main>
</template>

<script setup lang="ts">
import { ref } from "vue";

const checkboxArr = ref([
  { label: "Work desk, a good one. + nice chairs", value: false },
  { label: "Full height mirrors (in each room)", value: false },
  { label: "Oven", value: false },
  {
    label: "Good looking plates, + the more cooking stuff the better",
    value: false,
  },
  { label: "Hygienic shower", value: false },
  { label: "Green and good looking neighborhood", value: false },
  { label: "Any jogging area in 5 min walk radius", value: false },
  {
    label:
      "Wide bathroom, shower and other areas should be separated by doors, not by shower curtain",
    value: false,
  },
  {
    label: "Some place above a sink in the bathroom to put our stuff in there",
    value: false,
  },
  { label: "Furniture that does not fall apart and smells good", value: false },
  {
    label: "Distance from the center can’t be more than 3 USD cab ride",
    value: false,
  },
  {
    label:
      "There must be a clothes dryer and a washing machine without any mold in it",
    value: false,
  },
  { label: "Sleeping mattress must not be old or hurt you", value: false },
  {
    label:
      "If it’s usually hot outside, in each room should be an air conditioner",
    value: false,
  },
  {
    label: "Walls shouldn’t be dark or very colorful, just calming colors",
    value: false,
  },
  {
    label:
      "All necessary things about getting WIFI in the place should be made before we settle in",
    value: false,
  },
  {
    label:
      "At the porch, there shouldn’t be any kind of parking or cars gathering",
    value: false,
  },
  {
    label:
      "In general, the place should be wide, good looking, and new enough. Some cool design is welcome",
    value: false,
  },
]);

const percentChecked = ref(0);

const calcPercent = () => {
  const allProps = checkboxArr.value.length;
  const checkedProps = checkboxArr.value.filter((item) => item.value).length;
  percentChecked.value = Math.round((checkedProps / allProps) * 100);
};

calcPercent();
</script>

<style lang="scss">
body {
  overflow-x: hidden;
}
header {
  width: 100vw;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 22px;
  font-weight: 600;
}
.checkboxes__container {
  width: 100vw;
  max-width: 100vw;
  height: fit-content;
  display: grid;
  align-items: center;
  justify-items: flex-start;
  padding: 30px;
  overflow-x: hidden;

  .checkbox {
    display: grid;
    grid-template-columns: 20px 1fr;
    align-items: center;
    gap: 30px;
    p {
      font-size: 18px;
      word-break: break-all;
    }
  }
}
</style>
