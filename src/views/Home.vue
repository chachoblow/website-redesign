<template>
  <div class="home">
    <div id="image-wrapper" :style="menuStyle"></div>
    <Menu :menuItems="mainMenu" v-on:change-background="changeBackgrounds($event)"/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Menu from '@/components/Menu.vue'; // @ is an alias to /src

const mainMenu = [
  {
      id: 'comcis',
      title: 'Comics',
      backgroundImage: require('../assets/menu/comics-invert.jpg'),
  },
  {
      id: 'illustrations',
      title: 'Illustrations',
      backgroundImage: require('../assets/menu/illustrations-invert.jpg'),
  },
  {
      id: 'animations',
      title: 'Animations',
      backgroundImage: require('../assets/menu/animations-invert.jpg'),
  },
  {
      id: 'photos',
      title: 'Photos',
      backgroundImage: require('../assets/menu/photos-invert.jpg'),
  },
  {
      id: 'virtualFixtures',
      title: 'Virtual Fixtures',
      backgroundImage: require('../assets/menu/virtual-fixtures-invert.jpg'),
  },
  {
      id: 'findNeo',
      title: 'Find NEO',
      backgroundImage: require('../assets/menu/find-neo-invert.jpg'),
  },
  {
      id: 'lineCollection',
      title: 'Line Collection',
      backgroundImage: require('../assets/menu/line-collection-invert.jpg'),
  },
  {
      id: 'processingSketches',
      title: 'Processing Sketches',
      backgroundImage: require('../assets/menu/processing-sketches-invert.jpg'),
  },
];

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
