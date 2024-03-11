<template>
  <div
    :style="{
      display: 'flex',
      'flex-direction': 'column',
      gap: '16px',
    }"
  >
    <h2>Regular Video Player</h2>
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
      onShare: () => alert("share"),
      onBack: () => alert("back"),
      autoplay: true,
      type: "video",
      chromeCast: true,
      poster: "https://picsum.photos/200",
      ref: (el) => {
        this.videoRef = el;
      },
      languages: [
        {
          label: "GEO",
          title: "ქართული სერიალი",
          qualities: [
            {
              label: "1080p",
              sources: [
                {
                  // src: "https://uploader.1tv.ge/1tvplay/series/2021/1274/ge/64ff48a005b2e-1080p.mp4",
                  src: "https://uploader.1tv.ge/1tvplay/demo/test2.mp4"
                },
              ],
            },
            // {
            //   label: "720p",
            //   sources: [
            //     {
            //       src: "https://uploader.1tv.ge/1tvplay/series/2021/1274/ge/64ff53e88faee-720p.mp4",
            //     },
            //   ],
            // },
            // {
            //   label: "480p",
            //   sources: [
            //     {
            //       src: "https://uploader.1tv.ge/1tvplay/series/2021/1274/ge/64ff5d9256425-480p.mp4",
            //     },
            //   ],
            // },
          ],
        },
      ],
      onFinished: () => console.log("finished"),
    });

    return () => {
      player.dispose();
    };
  },

  methods: {
    playPause() {
      if (this.videoRef?.isPlaying()) {
        this.videoRef?.pause();
      } else {
        this.videoRef?.play();
      }
    },
    fastForward() {
      this.videoRef?.fastForward();
    },
    rewind() {
      this.videoRef?.rewind();
    },
  },
});
</script>
