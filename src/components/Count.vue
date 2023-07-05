<template>
  <div class="info">
    <h2 class="title">Count Per User</h2>
    <hr class="countline1"/>
  </div>
  <div class="calender">
    <p>Enter From Date and To Date to Filter</p>
    
    <!-- Calender Component -->
    <Calendar v-model="date" selectionMode="range" :minDate="minDate" :maxDate="maxDate" :manualInput="false"/>

    <!-- Button Component -->
    <Button label="Submit" @click="CheckClicked"/>
    <br><br><br>
    <hr class="countline2"/>
    <p>Showing Daily Deliverables Count Based on User</p>
    
  </div>
</template>

<script>
import Button from 'primevue/button';
import Calendar from 'primevue/calendar'

export default {
    components: {
        Calendar, Button,
    },
    methods : {
    CheckClicked() {
      console.log("U clicked me")
    }
  },
  data() {
    return {
    date: null,
    minDate: null,
    maxDate: null
  }
  },
  created() {
        let today = new Date();
        let month = today.getMonth();
        let year = today.getFullYear();
        let prevMonth = month === 0 ? 11 : month - 1;
        let prevYear = prevMonth === 11 ? year - 1 : year;

        this.minDate = new Date();
        this.minDate.setMonth(prevMonth);
        this.minDate.setFullYear(prevYear);
        this.maxDate = new Date();
        this.maxDate.setMonth(month);
        this.maxDate.setFullYear(year);
    }
}
</script>

<style>
    .title {
        margin: 20px;
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        font-weight: lighter;
        padding-left: 25px;
        font-size: 30px;

    }
    .countline1 , .countline2{
        height: 4.5px;
        margin: 0;
        background: grey;
        opacity: 0.3;
        margin-left: 25px;
        margin-right: 25px;
    }
    p {
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        font-weight: lighter;
        font-size: 15px;
        margin: 10px 25px;
        background-color: rgb(215, 234, 241);
    }
    
    .p-calendar {
        margin-left: 25px;
        width: 700px;
        float: left;
    }
    
    .p-button {
        margin-top: 25px;
        width: 700px;
    }
    
    label {
        margin-left: 30px;
        position: fixed;
    }
    
</style>