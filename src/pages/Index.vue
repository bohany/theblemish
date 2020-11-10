<template>
  <q-page class="flex flex-center">
    <video
      autoplay
      src="../assets/vidGorgeous.mp4"
      type="video/mp4"
      class="vidGorgeous"
      v-if="vidNum === 0"
      preload="auto"
      ref="vid0"
      playsinline
    />

    <video
      class="vidGhost"
      src="../assets/vidGhost.mp4"
      type="video/mp4"
      v-if="vidNum == 1"
      preload="auto"
      ref="vid1"
      autoplay
      playsinline
    />

    <video
      class="vidSayHi"
      src="../assets/vidSayHi.mp4"
      type="video/mp4"
      v-if="vidNum == 2"
      preload="auto"
      ref="vid2"
      autoplay
      playsinline
    />

    <q-btn
      round
      push
      color="deep-purple-6"
      icon="skip_next"
      id="skipBtn"
      size="1rem"
      @click="vidNext"
    />
    <q-btn
      glossy
      outline
      color="deep-purple-2"
      icon="play_circle_outline"
      id="playBtn"
      size="1.3rem"
      @click="play"
      v-if="vidNum === 0 && !gorgeousPlaying"
    />
  </q-page>
</template>

<script>
export default {
  name: "PageIndex",
  data() {
    return {
      vidNum: 0,
      gorgeousPlaying: false,
    };
  },
  methods: {
    vidNext() {
      this.vidNum += 1;
      if (this.vidNum > 2) {
        this.vidNum = 0;
      }
    },
    play() {
      this.gorgeousPlaying = true;
      this.$refs.vid0.play();
    },
  },
};
</script>
<style lang="sass" scoped>
.vidSayHi
  position: fixed
  left: -20
  top: -45%
  min-height: 150vh

.vidGorgeous
  position: fixed
  left: -20
  top: 0
  min-width: 100vw
  min-height: 100vh
.vidGhost
  position: fixed
  left: -20
  top: 0
  min-width: 100vw
  min-height: 100vh
#skipBtn
  position: fixed
  right: 8vmin
  bottom: 6vmin
  z-index: 200
#pauseBtn
  position: fixed
  left: 8vmin
  bottom: 6vmin
  z-index: 200
</style>

