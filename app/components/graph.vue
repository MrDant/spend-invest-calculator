<script setup>
import {
  Chart as ChartJS,
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Tooltip,
  Legend,
} from "chart.js";
import { Line } from "vue-chartjs";

ChartJS.register(
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Tooltip,
  Legend
);
const options = ref({
  responsive: true,
  maintainAspectRatio: false,
});

const props = defineProps(["data"]);
const params = computed(() => {
  return {
    datasets: props.data.map((e, i) => ({
      label: "Estimation " + (i + 1),
      backgroundColor:
        "#" +
        [...Array(6)]
          .map((e) => "0123456789ABCDEF"[Math.floor(Math.random() * 16)])
          .join(""),
      data: e,
    })),
  };
});
</script>
<template>
  <div>
    <div>
      <Line :options="options" :data="params" />
    </div>
  </div>
</template>
