<template>
    <div class="welcome-panel">
        <div class="time-panel">
            <h2 class="time" v-html="clock.time"></h2>
            <h3 class="date" v-html="clock.date"></h3>
        </div>
    </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class WelcomePanel extends Vue
{
    public clock: { date: string, time: string } = { date: "oof", time: "oww" };

    private timer = 0;

    public mounted()
    {
        this.timer = setInterval(this.update_clock.bind(this), 1000);
        this.update_clock();
    }
    public beforeDestroy()
    {
        clearInterval(this.timer);
    }

    public update_clock()
    {
        this.clock = this.get_clock();
    }
    public get_clock()
    {
        const now = new Date();
        return {
            date: now.toLocaleDateString("en-US", {
                weekday: "long",
                year: "numeric",
                // tslint:disable-next-line:object-literal-sort-keys
                month: "long",
                day: "numeric"
            }),
            time: now.toLocaleTimeString("en-US", {
                hour: "2-digit",
                hour12: false,
                minute: "2-digit"
            }).replace(/:/g, "<span class=\"blinker\">:</span>")
        };
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less">
.welcome-panel
{
    .time-panel
    {
        text-align: center;

        .time {
            font-size: 5rem;
        }
    }
}

@keyframes blinker
{
    0%   { opacity: 0; }
    50%  { opacity: 1; }
    100% { opacity: 0; }
}
.blinker { animation: blinker 1s step-start infinite; }
</style>
