<template>
    <div class="box has-text-weight-bold mt-3">
        <slot></slot>
    </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'BoxActivity',
})
</script>

<style scoped>
.box {
    background: #FAF0CA;
}
</style>
