<template>
    <div>Zaloguj się emailem
        <input type="text" v-model="email"/>
        <button @click="enter()">{{buttonLabelToDisplay}}</button>
    </div>
</template>

<script>
    export default {
        // mounted() {
        //     if (!this.buttonLabel) {
        //         this.buttonLabel = 'Zaloguj się';
        //     }
        // },
        computed: {
            buttonLabelToDisplay() {
                return this.buttonLabel || 'Zaloguj się';
            }
        },
        data() {
            return {
                email: ''
            }
        },
        props: ['buttonLabel'],
        methods: {
            enter() {
                this.$emit('login', this.email);
                this.email = '';
            }
        }
    }
</script>

<style scoped>

</style>