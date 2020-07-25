<template>
<div id="Demo">
    <div class='div-date'>
        <md-field>
        <label>Pick a Date</label>
        <md-input type="date" v-model="selectedDate" :value="selectedDate"></md-input>
        </md-field>
    </div>
    <div>
        <md-field>
        <label>Number of Days</label>
        <md-input id="numberDays" v-model="numberDays"></md-input>
        </md-field>
    </div>
    <div>
        <Calendar id="Calendar" :selectedDate="selectedDate" :numberDays="numberDays"/>
    </div>
</div>
</template>

<script>

import Calendar from './Calendar'

export default {
  name: "Demo",
  selectedDate: new Date(),
  components: {
      Calendar
  },
  data() {
      return {
          numberDays: 1,
          selectedDate: new Date()
      }
  },
}
</script>

<style>
.div-date {
    width: 10%;
}
</style>