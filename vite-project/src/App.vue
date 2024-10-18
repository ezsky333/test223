<template>
  <Artplayer @get-instance="getInstance" :option="option" :style="style" />
</template>

<script>
import Artplayer from "./components/Artplayer.vue";
import artplayerPluginLibass from 'artplayer-plugin-libass'
export default {
  data() {
    return {
      option: {
        container: '.artplayer-app',
        url: "https://emall.bydauto.com.cn/uploads/ueditor/1683508816350440.mp4",
        fullscreenWeb: true,
        subtitle: {
          url: 'https://artplayer.org/assets/sample/style-test.ass',
        },
        plugins: [
          artplayerPluginLibass({
            debug: true,
            workerUrl: './assets/subtitles-octopus-worker.js',
            wasmUrl: './assets/subtitles-octopus-worker.wasm',
            fallbackFont: './assets/SourceHanSansCN-Bold.woff2'
          }),
        ],
      },
      style: {
        width: "600px",
        height: "400px",
        margin: "60px auto 0",
      },
    };
  },
  components: {
    Artplayer,
  },
  methods: {
    getInstance(art) {
      console.info(art);
    },
  },
};
</script>