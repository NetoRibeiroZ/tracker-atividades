<template>
    <div>
        <div class="column">
            <div class="is-flex is-align-items-center is-justify-content-space-between">
                <button class="button" @click="startCounter()" :disabled="!buttonStop">
                    <span class="icon">
                        <i class="fas fa-play"></i>
                    </span>
                    <span>Play</span>
                </button>
                <button class="button ml-1" @click="stopCounter()" :disabled="buttonStop">
                    <span class="icon">
                        <i class="fas fa-stop"></i>
                    </span>
                    <span>Stop</span>
                </button>
                <TimerCount :time-sec="timeSec" />
            </div>
        </div>
    </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import TimerCount from './TimerCount.vue'

export default defineComponent({
    name: "StopWatch",
    data() {
        return {
            timeSec: 0,
            stopwatch: 0,
            buttonStop: true
        };
    },
    emits:['finishStopwatch'],
    methods: {
        startCounter() {
            if (this.buttonStop) {
                this.stopwatch = setInterval(() => {
                    this.timeSec++;
                }, 1000);
                this.buttonStop = false;
            }
        },
        stopCounter() {
            if (!this.buttonStop) {
                clearInterval(this.stopwatch);
                this.stopwatch = 0;
                this.buttonStop = true;
                this.$emit('finishStopwatch', this.timeSec);
                this. timeSec = 0;
            }
        }
    },
    components: {
        TimerCount,
    }
})
</script>
<style></style>