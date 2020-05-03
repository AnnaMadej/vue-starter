<template>
    <div>

        <button @click="addingMeeting=true" v-if="!addingMeeting">Dodaj nowe spotkanie</button>
        <new-meeting-form @added="addNewMeeting($event)" v-if="addingMeeting"/>
        <meetings-list :loggedUser="loggedUser" :meetings="meetings" @enroll="enrollToMeeting($event)"
                       @leave="leaveMeeting($event)"
                       @remove="removeMeeting($event)"
                       v-if="meetings.length>0"/>

        <div v-else>Brak zaplanowanych spotkań</div>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";


    export default {
        components: {NewMeetingForm, MeetingsList},
        name: "MeetingPage.vue",
        props: ['loggedUser'],
        data() {
            return {
                meetings: [],
                addingMeeting: false
            }
        },
        methods: {
            addNewMeeting(meeting) {
                this.meetings.push(meeting);
                this.addingMeeting = false;
            },
            enrollToMeeting(meetingName) {
                let meeting;
                for (let i = 0; i < this.meetings.length; i++) {
                    meeting = this.meetings[i];
                    if (meeting.name === meetingName) {
                        meeting.participants.push(this.loggedUser);
                    }
                }
            },
            leaveMeeting(meetingName) {
                let meeting;
                for (let i = 0; i < this.meetings.length; i++) {
                    meeting = this.meetings[i];
                    if (meeting.name === meetingName) {
                        meeting.participants.splice(meeting.participants.indexOf(meeting), 1);
                    }
                }
            },
            removeMeeting(meetingName) {
                for (let i = 0; i < this.meetings.length; i++) {
                    if (this.meetings[i].name === meetingName) {
                        this.meetings.splice(i, 1);
                    }
                }
            }
        }
    }
</script>

<style scoped>

</style>