<template>
  <q-layout view="hHh lpR fFf">
    <q-header reveal style="background-color: transparent; top: 1vh">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
          size="md"
        />

        <q-toolbar-title class="text-weight-bold">The Blemish</q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      overlay
      behavior="mobile"
      elevated
      :width="180"
      dark
    >
      <q-list>
        <q-item-label
          header
          class="text-grey-2 text-h6"
          @click="leftDrawerOpen = !leftDrawerOpen"
        >
          Follow us:
        </q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <div class="logoContainer">
      <img id="logo" alt="Blemish logo" src="~assets/logoHQ.png" />
    </div>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from "components/EssentialLink.vue";

const linksData = [
  {
    title: "Spotify",
    icon: "headset",
    link:
      "https://open.spotify.com/artist/0brQOK8RR5HSVwZJlqWYD7?si=wbvDOmIJQCK9FKWJiiCTkA",
  },
  {
    title: "iTunes",
    icon: "album",
    link: "https://apple.co/3lfHLox",
  },
  {
    title: "Instagram",
    icon: "collections",
    link: "https://www.instagram.com/blemishofficial/",
  },
  {
    title: "Facebook",
    icon: "thumb_up",
    link: "https://www.facebook.com/BlemishOfficial/",
  },
  {
    title: "Youtube",
    icon: "play_circle_outline",
    link: "https://www.youtube.com/channel/UClX-QDbKYCtbl1Lj8R1KyVw",
  },
];

export default {
  name: "MainLayout",
  components: { EssentialLink },
  data() {
    return {
      leftDrawerOpen: false,
      essentialLinks: linksData,
    };
  },
};
</script>
<style lang="sass" scoped>
#logo
  width: 44vmin
.logoContainer
  position: absolute
  right: 7vmin
  bottom: 4vmin
  z-index: 10
</style>
