<template>
<div id="Calendar">
    <v-calendar ref="calendar" :attributes="attr" :key="generateKey(selectedDate, numberDays)" :firstDayOfWeek=1 :rows="4" columns="4"></v-calendar>
</div>
</template>

<script>
export default {
  name: "Calendar",
  props: [ 'selectedDate', 'numberDays' ],
  data() {
    const holidays = [
      {
        description: 'Christmas',
        dates: { 
          start: new Date('12/25/1900'),
          monthlyInterval: 12
        },
        dot: {
            color: 'red',
            class: 'my-dot-class',
        },
      },
    ];
    return {
      attr: [
        // Highlights selected day
        {
          key: 'today',
          highlight: 'blue',
          dates: [
            {
              start: this.selectedDate, span: this.numberDays
            }
          ]
        },
        // Highlights weekends
        {
          highlight: 'yellow',
          dates: [
            {
              weekdays: [ 1, 7]
            }
          ]
        },
        // Highlights weekdays
        {
          highlight: 'green',
          dates: [
            {
              weekdays: [ 2, 3, 4, 5, 6]
            }
          ]
        },
      ]
    }
  },
  // Adds watch on both props to update calendar when they change
  watch: {
    numberDays(nbDays) {
      if (nbDays != 0)
        this.attr[0].dates[0].span = nbDays
      else
        this.attr[0].dates[0].span = 1
    },
    selectedDate(date) {
      date = new Date(date)

      if (date) {
        this.attr[0].dates[0].start = new Date(date.getFullYear(), date.getMonth(), date.getDate()+1)
      }
      else
        this.attr[0].dates[0].start = new Date()
    }
  },
  // Moves calendar to the selected date
  async updated() {
    var calendar = this.$refs.calendar
    await calendar.move(this.selectedDate)
  },
  // Generates a unique key for calendar component this way updates happen when Date or Days change
  methods: {
    generateKey(date, days) {
      const uniqueKey = `${date}-${days}`;
      return uniqueKey;
    }
  }
}
</script>