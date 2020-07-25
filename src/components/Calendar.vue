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
        {
          key: 'today',
          highlight: 'blue',
          dates: [
            {
              start: this.selectedDate, span: this.numberDays
            }
          ]
        },
        {
          highlight: 'yellow',
          dates: [
            {
              weekdays: [ 1, 7]
            }
          ]
        },
        {
          highlight: 'green',
          dates: [
            {
              weekdays: [ 2, 3, 4, 5, 6]
            }
          ]
        },
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

      this.nbRows = Math.ceil(this.numberDays/30)

    }
  },
  async updated() {
    var calendar = this.$refs.calendar
    await calendar.move(this.selectedDate)
  },
  methods: {
    generateKey(date, days) {
      const uniqueKey = `${date}-${days}`;
      return uniqueKey;
    }
  }
}
</script>