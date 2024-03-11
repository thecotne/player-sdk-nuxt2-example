<template>
  <div
    :style="{
      'max-width': '1000px',
      margin: '20px auto',
      display: 'flex',
      'flex-direction': 'column',
      gap: '32px',
    }"
  >
    <!-- <AudioPlayer /> -->
    <SolidPlayer />
    <!-- <ExternalControls /> -->
    <!-- <HlsPlayer /> -->
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "IndexPage",
});
</script>
