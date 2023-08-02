<template>
    <div>
        <BoxActivity class="box has-text-weight-bold">
            <div class="columns">
                <div  class="column is-7">
                    <p>{{activity.description || 'Atividade sem descrição'}}</p>
                </div>
            </div>
            <div class="column">
                <TimerCount :alternativeDark="true" :timeSec="activity.timeSec"/>
            </div>
        </BoxActivity>
    </div>
</template>
<script lang="ts">
import { defineComponent, PropType } from 'vue';
import TimerCount from './TimerCount.vue';
import IActivity from '../Interfaces/IActivity';
import BoxActivity from './BoxActivity.vue';

export default defineComponent({
    name: 'ActivityCard',
    props: {
        activity: {
            type: Object as PropType<IActivity>,
            required: true
        }
    },
    components: {
    TimerCount,
    BoxActivity
}
})

</script>
<style>
.display-card{
    color: #000 !important;
}
</style>
