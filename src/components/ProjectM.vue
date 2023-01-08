<script setup lang="ts">
import { ref, onMounted } from "vue";
import avPluginProjectM from "av-plugin-projectm";

const canvasEl = ref();
let avPlugin: avPluginProjectM;

onMounted(async () => {
  const canvas = {
    canvas: canvasEl.value,
    wasmFilepath: "assets/wasm/av_plugin_projectm_wasm_rs.wasm",
  };

  avPlugin = new avPluginProjectM(canvas);

  await avPlugin.initialize();
  console.log(await avPlugin);
}); 
</script>

<template>
  <div class="projectm">
    <canvas
      id="canvas"
      ref="canvasEl"
      oncontextmenu="event.preventDefault()"
      tabindex="-1"
    ></canvas>
  </div>
</template>
