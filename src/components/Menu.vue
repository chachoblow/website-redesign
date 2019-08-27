<template>
    <div class="main-menu">
        <nav>
            <ol> 
                <li v-for="item in menuItems" :key="item.id">
                    <!-- Hacky way to preload images -->
                    <img class='preload' :src="item.backgroundImage" />
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

<script lang='ts'>
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class Menu extends Vue {
    @Prop()
    private menuItems!: string;
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