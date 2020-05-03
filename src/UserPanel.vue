<template>
    <div class="row">
        <h2 class="column">Witaj {{userName}}!</h2>
        <span class="column column-33 right"> <button @click="exit()"
                                                      class="button button-outline">Wyloguj</button></span>
    </div>
</template>

<script>
    export default {
        Data() {

        },
        props: ['userName'],
        methods: {
            exit() {
                this.$emit('logout');
            }
        }
    }
</script>

<style scoped>

</style>
<style>

    .right {
        text-align: right;
        margin-right: 1em;
    }
</style>