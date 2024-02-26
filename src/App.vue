<template>
  <b-container fluid>
    <div>
      <canvas id="canvas" width="800" height="800"></canvas>
    </div>
  </b-container>
</template>

<script>
import CanvasXpress from "canvasxpress";

export default {
  mounted() {
    console.log(CanvasXpress);
    this.loaddata();
  },
  methods: {
    loaddata() {
      new CanvasXpress.init(
        "canvas",
        {
          y: {
            data: [[10, 100, 70, 130, 60]],
            vars: ["A"],
            smps: ["S1", "S2", "S3", "S4", "S5"],
          },
        },
        {
          background: "rgb(255,255,255)",
          colorScheme: "CanvasXpress",
          graphOrientation: "vertical",
          graphType: "Area",
          objectBorderColor: false,
          plotBox: false,
          plotBoxColor: "rgb(204,204,204)",
          showLegend: false,
          showLegendBorder: true,
          smpLabelRotate: 90,
          smpTitle: "time",
          xAxis: ["A"],
        },
        false
      );
    },
  },
};
</script>

<style scoped>
</style>
