<template>
  <div class="container">
    <Clock
      :date="startTime" 
      @start-time="start"
      @pause-time="pause"
      @stop-time="finish"/>
    <History />
    <!-- <p>Hora de Inicio: {{ startTime }}</p>
    <p>Tiempo de trabajo: {{ hours }}:{{ minutes }}:{{ seconds }}</p>
    <p>Hora de Final: {{ finishTime }}</p> -->
  </div>
</template>

<script>
import dayjs from 'dayjs'
import Clock from '~/components/Clock'
import History from '~/components/History.vue'

export default {
  data () {
    return {
      startTime: null,
      finishTime: null,
      counterSeconds: 0,
      counterMinutes: 0,
      counterHours: 0,
      timer: null
    }
  },

  components: {
    Clock,
    History
  },

  computed: {
    seconds () {
      return this.counterSeconds.toString().length === 1
        ? `0${this.counterSeconds}`
        : this.counterSeconds
    },
    minutes () {
      return this.counterMinutes.toString().length === 1
        ? `0${this.counterMinutes}`
        : this.counterMinutes
    },
    hours () {
      return this.counterHours.toString().length === 1
        ? `0${this.counterHours}`
        : this.counterHours
    }
  },

  methods: {
    start () {
      this.startTime = dayjs().format('HH:mm')
      this.counter()
    },

    pause () {
      console.log('PAUSE')
    },

    finish () {
      this.finishTime = dayjs().format('HH:mm')
      clearInterval(this.timer)
    },

    counter () {
      this.timer = setInterval(() => {
        this.counterSeconds++
        if (this.counterSeconds === 60) {
          this.counterSeconds = 0
          this.counterMinutes++
        }
        if (this.counterMinutes === 60) {
          this.counterMinutes = 0
          this.counterHours++
        }
      }, 1000)
    }
  }
}
</script>

<style>
  .container {
    display: flex;
    justify-content: center;
  }
</style>
