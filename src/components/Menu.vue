<template>
    <div class="main-menu">
        <nav>
            <ol> 
                <li v-for="item in mainMenu" :key="item.id">
                    <!-- Hacky way to preload images -->
                    <img class="preload" :src="item.backgroundImage" />
                    <a 
                        class="nav-option" 
                        @mouseover="$emit('change-background', item.backgroundImage)"
                        @mouseout="$emit('change-background', 'none')"
                    >{{ item.title }}</a>
                </li>
            </ol>
        </nav>
    </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class Menu extends Vue {
    private mainMenu = [
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
}
</script>

<style lang="scss">
.main-menu {
    padding-top: 0;
    width: 100%;
    min-height: 100vh;
    display: flex;
}

nav {
    margin: auto;
    padding: 75px 0;
    align-items: center;
}

nav ol{
    list-style: none;
    counter-reset: counter;
    padding: 0;
    margin: 0;
}

nav ol li {
    counter-increment: counter;
    font-size: 5em;
    font-weight: 600;
    margin: 0;
    padding: 0.2em 0;

    &:before {
        font-family: 'IBM Plex Mono', monospace;
        content: counter(counter) ". ";
        color: black;
        font-size: 0.25em;
        font-weight: 200;
    }
}

a.nav-option {
    text-decoration: none;
    color: white;
    mix-blend-mode: difference;

    &:hover {
        text-decoration: line-through;
        text-decoration-color: gold;
        cursor: pointer;
    }
}

.preload {
    display: none;
}
</style>