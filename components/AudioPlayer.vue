<template>
  <div
    :style="{
      display: 'flex',
      'flex-direction': 'column',
      gap: '16px',
    }"
  >
    <h2>Regular Audio Player</h2>
    <div ref="player" />
  </div>
</template>

<script>
import Vue from "vue";

export default Vue.extend({
  mounted() {
    const player = XSG.createPlayer(this.$refs.player, {
      type: "audio",
      autoPlay: true,
      poster: "https://picsum.photos/200",
      languages: [
        {
          label: "GEO",
          qualities: [
            {
              label: "720p",
              sources: [
                {
                  src: "https://uploader.1tv.ge/1tvplay/demo/demo.mp3",
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
