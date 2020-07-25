<template>
  <div class="home">
    <h1>Programming Exercise UI Devs</h1>
    <p>Develop a web-based application that displays a monthly calendar based on the requirements below. 
      It is NOT important that you actually complete this exercise fast. 
      It IS important that you demonstrate a fundamentally sound approach for the development of this application.
      Please use client-side technologies only. If a link to a published working solution is not provided the exercise will not 
      be evaluated.</p>
      <h2>Detailed Requirements:</h2>
      <ul class="ul-req">
        <li>Allow the user to specify three inputs: A Start Date, the Number of days to display and a Country Code literal 
          (the country code literal value must be defined by the user with the keyboard).
          <br>
          <br>
          <span>
            Example:
            <br>
            Start Date: 8/15/2008
            <br>
            Number of days: 17
            <br>
            Country Code: US
          </span>
        </li>
        <br>
        <br>
        <li>
          Render a calendar that spans as many weeks as necessary in order to cover the defined number of days. 
          If the date range spans months, a new header needs to be created for that month. The Calendar should display its days 
          starting on Sunday and ending on Saturday, as shown below. This should work with any number of days regardless of the 
          years meaning that if the user specifies more than 365 days, calendars will be generated accordingly for the next year 
          and so on.
        </li>
        <br>
        <br>
        <li>
          The days should be color coded as follows: 
          <br>
          A.	Weekends are yellow. 
          <br>
          B.	Weekdays are green. 
          <br>
          C.	Invalid days are hidden and the background should be gray.
          <br>
          <br>
          Invalid days are defined as:
          <br>
          D.	Any days in the week previous to the Start date.
          <br>
          E.	Any days in the week after the last rendered day.
          <br>
          F.	Any days before the first day of the month (if the calendar spills into another month).
        </li>
        <br>
        <li>
          <b>Extra credit</b> will be given for adding Holidays in a different color.
        </li>
      </ul>
  </div>
</template>

<script>
export default {
  name: 'Home',
}
</script>

<style>
.ul-req {
  list-style: circle;
  text-align: left;
}
</style>
