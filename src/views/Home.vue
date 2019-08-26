<template>
  <div class="home">
    <div id="image-wrapper" :style="menuStyle"></div>
    <Menu v-on:change-background="changeBackgrounds($event)"/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Menu from '@/components/Menu.vue'; // @ is an alias to /src

@Component({
  components: {
    Menu,
  },
})

export default class Home extends Vue {
  private defaultBackgroundImage: string = require('../assets/menu/slit-scan-invert.jpg');
  private backgroundImage: string = this.defaultBackgroundImage;

  private changeBackgrounds(image: string) {
    this.backgroundImage = (image === 'none') ? this.defaultBackgroundImage : image;
  }

  // Computed
  get menuStyle() {
    return {
      backgroundImage: 'url(' + this.backgroundImage + ')',
    };
  }
}
</script>

<style lang="scss">
.home {
  position: absolute;
  top: 0;
  left: 0;
  min-width: 100%;
  min-height: 100vh;

  background-color: white;
  background-position: center;
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-size: auto 70vh;

  z-index: -2;
  text-transform: uppercase;
}

 #image-wrapper {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;

  transition: background-image 0.25s ease-in-out;
  background-position: center;
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-size: auto 70vh;
  mix-blend-mode: difference;
  z-index: -1;
}
</style>
