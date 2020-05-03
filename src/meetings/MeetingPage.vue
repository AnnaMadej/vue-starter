<template>
    <div >

        <button v-if="!addingMeeting" @click="addingMeeting=true">Dodaj nowe spotkanie</button>
        <new-meeting-form v-if="addingMeeting" @added="addNewMeeting($event)"/>
        <meetings-list v-if="meetings.length!=0" :meetings="meetings" :loggedUser="loggedUser"
                       @enroll="enrollToMeeting($event)"
                       @leave="leaveMeeting($event)"
                       @remove="removeMeeting($event)"/>

        <div v-if="meetings.length==0">Brak zaplanowanych spotkań</div>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";



    export default {
        components: {NewMeetingForm, MeetingsList},
        name: "MeetingPage.vue",
        props: ['loggedUser'],
        data(){
            return{
                meetings: [],
                addingMeeting: false
            }
        },
        methods: {
            addNewMeeting(meeting){
                this.meetings.push(meeting);
                this.addingMeeting = false;
            },
            enrollToMeeting(meetingName){
                var meeting;
                for (var i = 0; i < this.meetings.length; i++) {
                    meeting = this.meetings[i];
                    if (meeting.name === meetingName) {
                        meeting.participants.push(this.loggedUser);
                    }
                }
            },
            leaveMeeting(meetingName){
                let meeting;
                for (let i = 0; i < this.meetings.length; i++) {
                    meeting = this.meetings[i];
                    if (meeting.name === meetingName) {
                        meeting.participants.splice(meeting.participants.indexOf(meeting), 1);
                    }
                }
            },
            removeMeeting(meetingName){
                for (var i = 0; i < this.meetings.length; i++) {
                    if(this.meetings[i].name===meetingName){
                        this.meetings.splice(i,1);
                    }
                }
            }
        }
    }
</script>

<style scoped>

</style>