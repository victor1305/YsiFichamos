<template>
  <div class="clock-container">
    <div class="logo-container">
      <img class="logo" src="/ysi_negative.svg" alt="logo-Ysi"/>
    </div>
    <div class="buttons-container">
      <button v-if="!clockState" @click="start">¡A por el día!</button>
      <button v-if="clockState" @click="pause">Break time</button>
      <button v-if="clockState" @click="stop">¡Lo dejo por hoy!</button>
    </div>  
  </div>
</template>

<script>
export default {

  data () {
    return {
      clockState: false
    }
  },

  methods: {
    start () {
      this.$emit('start-time')
      this.clockState = true
    },
    pause () {
      this.$emit('pause-time')
      this.clockState = false
    },
    stop () {
      this.$emit('stop-time')
      this.clockState = false
    }
  }

}
</script>

<style>
  .clock-container {
    width: 200px;
    padding: 25px;
    margin-top: 100px;
    border: 1px solid black
  }

  .logo-container {
    padding-bottom: 45px;
  }

  .logo {
    width: 75px;
  }
</style>