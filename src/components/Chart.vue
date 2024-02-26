<template>
  <div>
    <h1>Bar Chart with CanvasXpress</h1>
    <div>
      <canvas 
        :id='target'
        :height='height'
        :width='width'
      >
      </canvas>
    </div>
  </div>
</template>

<script>
  import CanvasXpress from 'canvasxpress';
  export default {
    name: "BarChart",
    props: ["barData"],
    created() {
      this.target = this.target ? this.target : false
      this.data = this.data ? this.data : false
      this.config = this.config ? this.config : false
      this.events = this.events ? this.event : false
      this.width = this.width ? this.width : 800
      this.height = this.height ? this.height : 800
    },
    mounted() {
      //Create graph and render
      this.graph = new CanvasXpress.init(
        this.target,
        this.data,
        this.config,
        this.events
      )
      if (this.onRef) {
        this.onRef(this.graph)
      }
    },
    updated() {
      //Update Graph Options & Data
      this.graph.resetConfig()
      this.graph.updateConfig(this.config)
      this.graph.updateData(this.data)
    },
    destroyed() {
      //Destroy graph and remove reference
      this.graph.destroy()
      if (this.onRef) {
        this.onRef(undefined)
      }
    },
    render() {
      return {
        id: this.target,
        width: this.width,
        height: this.height
      }
    }
  }
</script>