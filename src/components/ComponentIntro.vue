<template>
    <v-container>
        <v-row class="white--text">
            <v-col>
                <p></p>
                <p>
                    01 AU COMMENCEMENT, L'Homme créa le Web.
                    <span class="font-weight-bold">le web</span>
                </p>
            </v-col>
        </v-row>
        <v-row v-if="stepSup1" class="white--text">
            <v-col class="text-right">
                <p>02 Le Web était informe et vide, les pixels blanc étaient au-dessus de l’abîme</p>
            </v-col>
        </v-row>
        <v-row v-if="stepSup2" class="white--text">
            <v-col class="text-center">
                <p>
                    03 L'homme dit : « Que la couleurs soit. »
                    <span
                        class="blue--text"
                    >Et la couleurs fut</span>
                </p>
            </v-col>
        </v-row>
        <v-row v-if="stepSup3" class="white black--text">
            <v-col>
                <p>04 L'homme vit que la lumière était bonne, et L'Homme sépara la lumière des ténèbres.</p>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
export default {
    name: "componentIntro",

    data: () => ({
        step: 0,
        timingApparition: 3000
    }),
    computed: {
        stepSup1() {
            return this.step >= 1;
        },
        stepSup2() {
            return this.step >= 2;
        },
        stepSup3() {
            return this.step >= 3;
        }
    },
    mounted() {
        setTimeout(() => this.callBackStep(), this.timingApparition);
    },
    methods: {
        callBackStep() {
            let newStep = this.step + 1;
            this.step = newStep;
            if (newStep <= 3) {
                setTimeout(() => this.callBackStep(), this.timingApparition);
            } else {
                this.$emit("endTimer");
            }
        }
    }
};
</script>
