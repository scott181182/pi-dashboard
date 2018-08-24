<template>
    <div id="app" class="tile is-ancester">
        <div class="tile is-4 is-parent is-vertical">
            <div class="tile is-child">
                <Welcome/>
            </div>
            <div class="tile is-child"></div>
        </div>
        <div class="tile is-4 is-parent is-vertical">
            <div class="tile is-child"></div>
            <div class="tile is-child"></div>
        </div>
        <div class="tile is-4 is-parent is-vertical">
            <div class="tile is-child"></div>
            <div class="tile is-child"></div>
        </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

import Welcome from "./components/Welcome.vue";

@Component({
    components: {
        Welcome
    }
})
export default class App extends Vue {  }
</script>

<style lang="less">
html, body {
    height: 100%;
    overflow: hidden;
}
#app
{
    height: 100%;

    color: #2c3e50;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;

    .tile.is-parent {
        padding: 0;

        .tile.is-child {
            height: 50%;
            overflow: auto;

            padding: 1rem;
            border: 1px solid #ddd;
            margin: 0 !important;
        }
    }
}
</style>
