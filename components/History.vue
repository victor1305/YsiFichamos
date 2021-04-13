<template>
  <div class="history-container">
    <div class="day-container"> 
      <h4>{{ date }}</h4>
      <p>La jornada ha comenzado a las {{ startTime }}</p>
    </div>
  </div>
</template>

<script>
export default {

  data() {
    return {
      date: '25/03/2021',
      startTime: '08.00'
    }
  },

  methods: {

  }
}
</script>

<style>
  .history-container {
    margin-top: 100px;
    margin-left: 50px;
    width: 60%;
    border: 2px solid #e3286e;
    border-radius: 15px;
    padding: 10px 0px
  }

  .day-container {
    border-bottom: 1px solid black;
    padding: 0 20px;
  }
</style>