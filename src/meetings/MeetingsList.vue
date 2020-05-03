<template>
    <div>
        <h3>Zaplanowane zajęcia ({{meetings.length}})</h3>
        <table v-if="meetings.length > 0">
            <thead>
            <tr class="row">
                <th class="column column-10">Nazwa spotkania</th>
                <th class="column">Opis</th>
                <th class="column">Uczestnicy</th>
                <th class="column column-33"/>
            </tr>
            </thead>
            <tbody>
            <tr :key="meeting.name" class="row" v-for="meeting in meetings">
                <td class="column column-10">{{ meeting.name }}</td>
                <td class="column">{{ meeting.description }}</td>

                <td class="column">
                    <ul v-for="participant in meeting.participants">
                        <li> {{participant}}</li>
                    </ul>

                </td>
                <td class="column column-33 right">
                    <button @click="enroll(meeting.name)" class="button button-outline "
                            v-if="!userEnrolled(meeting.participants)">Zapisz się
                    </button>
                    <button @click="leave(meeting.name)" class="button button-outline"
                            v-if="userEnrolled(meeting.participants)">Wypisz się
                    </button> &nbsp;
                    <button @click="remove(meeting.name)" v-if="meeting.participants.length===0">Usuń puste
                        spotkanie
                    </button>
                </td>
            </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
    export default {
        props: ['meetings', 'loggedUser'],
        methods: {
            enroll(meetingName) {
                this.$emit('enroll', meetingName);
            },
            leave(meetingName) {
                this.$emit('leave', meetingName);
            },
            userEnrolled(participants) {
                if (participants == null || participants.length === 0) return false;
                return participants.includes(this.loggedUser);
            },
            remove(meetingName) {
                this.$emit("remove", meetingName);
            }
        }
    }
</script>

<style>

    .right {
        text-align: right;
        margin-right: 1em;
    }
</style>