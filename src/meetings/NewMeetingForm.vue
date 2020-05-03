<template>
    <form @submit.prevent="addNewMeeting()">
        <h3>Dodaj nowe spotkanie</h3>
        <label>Nazwa</label>
        <input type="text" v-model="newMeeting.name">
        <label>Opis</label>
        <textarea v-model="newMeeting.description"/>
        <button>Dodaj</button>
        <span class="error" v-if="emptyNameError">Spotkanie musi mieć nazwę!</span>
    </form>
</template>

<script>


    export default {
        data() {
            return {
                newMeeting: {
                    name: '',
                    description: '',
                    participants: [],
                },
                emptyNameError: false
            };
        },
        methods: {
            addNewMeeting() {
                if (this.newMeeting.name) {
                    this.$emit('added', Object.assign({}, this.newMeeting));
                    this.newMeeting.name = '';
                    this.newMeeting.description = '';
                    this.newMeeting.participants = [];
                } else {
                    this.emptyNameError = true;
                }


            }
        }
    }
</script>

<style scoped>
    .error {
        color: red;
    }

</style>