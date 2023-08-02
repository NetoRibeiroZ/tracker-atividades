<template >
    <div class="box form">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Form for create new task">
                <input type="text" class="input" placeholder="Qual tarefa Deseja Realizar?" v-model="descriptionAtivity">
            </div>
            <StopWatch @finish-stopwatch="finishEvent" />
        </div>
    </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import StopWatch from './StopWatch.vue'
export default defineComponent({
    components: {
        StopWatch,
    },
    emits:['onSaveActivity'],
    data() {
        return {
            descriptionAtivity: ''
        }
    },
    methods: {
        finishEvent(timeSec: number): void {
            this.$emit('onSaveActivity',{
                timeSec: timeSec,
                description: this.descriptionAtivity 
            })
            this.descriptionAtivity = '';
        },
    },

})
</script>
<style scoped>
.form{
color: var(--Text-primary);
background-color: var(--bg-primary);
}
</style>