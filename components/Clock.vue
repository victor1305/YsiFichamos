<template>
  <div class="clock-container">
    <div class="logo-container">
      <img class="logo" src="/ysi_negative.svg" alt="logo-Ysi"/>
      <h4>¿Fichamos?</h4>
    </div>
    <div v-if="!state" class="buttons-container">
      <button class="btn-menu" v-if="!clockState" @click="preStart">¡A por el día!</button>
      <button class="btn-menu" v-if="clockState" @click="prePause">Break time</button>
      <button class="btn-menu" v-if="clockState" @click="stop">¡Lo dejo por hoy!</button>
    </div>  
    <div v-if="state === 'start'">
      <button class="btn-menu" @click="start">Desarrollo</button>
      <button class="btn-menu" @click="start">Diseño</button>
      <button class="btn-menu" @click="start">BBDD</button>
      <button class="btn-menu" @click="start">RRSS y Contenidos</button>
      <button class="btn-menu" @click="start">Sin Proyecto</button>
    </div>
    <div v-if="state === 'pause'">
      <button class="btn-menu" @click="pause">¡A Comer!</button>
      <button class="btn-menu" @click="pause">Descanso</button>
      <button class="btn-menu" @click="pause">Otros Motivos</button>
    </div>
  </div>
</template>

<script>
import Modal from '~/components/Modal'
export default {

  components: {
    Modal
  },

  data () {
    return {
      clockState: false,
      modalState: false,
      state: ''
    }
  },

  methods: {
    preStart () {
      this.state = 'start'
    },
    prePause () {
      this.state = 'pause'
    },
    start () {
      //this.modalState = true
      this.$emit('start-time')
      this.clockState = true
      this.state = ''
    },
    pause () {
      this.$emit('pause-time')
      this.clockState = false
      this.state = ''
    },
    stop () {
      this.$emit('stop-time')
      this.clockState = false
    },
    closeModal () {
      //this.modalState = false
    }
  }

}
</script>

<style>
  h4 {
    font-size: 20px;  
    margin: 10px;
  }

  .clock-container {
    width: 200px;
    padding: 25px;
    margin-top: 100px;
    border: 2px solid #e3286e;
    border-radius: 15px;
  }

  .logo-container {
    padding-bottom: 25px;
    align-items: center;
    text-align: center;
  }

  .logo {
    width: 105px;
    margin-bottom: 10px;
  }
</style>