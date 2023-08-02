<template >
    <div class="ml-3">
        <section>
            <strong class="display" :class="{'display-dark':alternativeDark}">
                {{ timeSpend }}
            </strong>
        </section>
    </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: "TimerCount",
    props:{
        timeSec:{
            type: Number,
            default: 0,
        }, 
        alternativeDark:{
            type: Boolean,
            default: false
        } 
    },
    computed: {
        timeSpend(): string {
            return new Date(this.timeSec * 1000).toISOString().substr(11, 8)
        }
    }
})
</script>
<style scoped>
.display{
    color: var(--Text-primary);
}
.display-dark{
    color: #000;
}
</style>