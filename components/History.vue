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
    margin-left: 50px;
    width: 60%;
    border: 1px solid black;
    padding: 10px 20px
  }
</style>