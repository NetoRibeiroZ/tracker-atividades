<template >
    <header>
        <h1>
            <img src="../assets/logo.png" alt="Logo do projeto">
        </h1>
        <h1 class="has-text-centered mt-10"> <button class="button" @click="changeTheme">
                {{ textButton }}
            </button></h1>
    </header>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'SideBar',
    emit: ['changeTheme'],
    data() {
        return {
            darkMode: false
        }
    },
    methods: {
        changeTheme() {
            this.darkMode = !this.darkMode;
            this.$emit('changeTheme', this.darkMode)
        }
    },
    computed: {
        textButton() {
            if (this.darkMode) {
                return 'Dark mode off'
            }
            return 'Dark mode on'
        }
    }
})
</script>
<style scoped>
header {
    background-color: #34849c;
    width: 100%;
    height: 100vh;
}

@media only screen and (max-width: 768) {
    .header {
        padding: 2.5rem;
        height: auto;
    }
}
</style>
