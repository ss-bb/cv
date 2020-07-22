<template>
    <v-app id="test" :class="{ 'forced__black': isActive }">
        <v-app-bar app color="primary" dark v-if="passStep1"></v-app-bar>
        <v-main>
            <ComponentIntro @endTimer="endtimer" />
        </v-main>
    </v-app>
</template>

<script>
import ComponentIntro from "./components/ComponentIntro";

export default {
    name: "App",
    components: {
        ComponentIntro
    },
    data: () => ({
        //
    }),
    computed: {
        isActive() {
            console.log("a", this.currentStep == 1);
            return this.currentStep == 1;
        },
        passStep1() {
            return this.currentStep >= 2;
        },
        currentStep() {
            return 1;
        }
    },
    methods: {
        endtimer() {
            console.log("this is the end");
        }
    }
};
</script>

<style lang="scss" scoped>
.forced__black {
    background-color: black !important;
}
</style>