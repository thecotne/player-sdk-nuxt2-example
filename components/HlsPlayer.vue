<template>
  <div
    :style="{
      display: 'flex',
      'flex-direction': 'column',
      gap: '16px',
    }"
  >
    <h2>HLS Player (can Chrome Cast when on the same Wi-Fi with a device)</h2>
    <div ref="player" />
  </div>
</template>

<script>
import Vue from "vue";

export default Vue.extend({
  data() {
    return {
      videoRef: null,
    };
  },

  mounted() {
    const player = XSG.createPlayer(this.$refs.player, {
      hls: true,
      autoplay: true,
      chromeCast: true,
      type: "video",
      ref: (el) => {
        this.videoRef = el;
      },
      languages: [
        {
          label: "GEO",
          qualities: [
            {
              label: "1080p",
              sources: [
                {
                  src: "https://tv.cdn.xsg.ge/gpb-1tv/index.m3u8",
                },
              ],
            },
          ],
        },
      ],
      onFinished: () => console.log("finished"),
    });

    return () => {
      player.dispose();
    };
  },
});
</script>
