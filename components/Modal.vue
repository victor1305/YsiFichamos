<template>
  <div
    class="modal"
    :class="{ 'modal--show': isModalOpen }"
    @click="$emit('cancel')">
    <div class="modal__content" :style="style" @click.stop="() => {}">
      <div v-if="closeModalX" class="modal__content__close" @click="$emit('cancel')">
        <i class="mdi mdi-close text-danger"></i>
      </div>
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    isModalOpen: {
      type: Boolean,
      default: false
    },
    closeModalX: {
      type: Boolean,
      default: true
    },
    widthPx: {
      type: String,
      default: '671px'
    }
  },
  computed: {
    style () {
      return `max-width: ${this.widthPx}`
    }
  },
}
</script>

 <style lang="scss" scoped>

 .modal {
  left: -9999px;
  height: 100vh;
  width: 100vw;
  opacity: 0;
  transition: .1s opacity;
  background-color: rgba(0,0,0,.3);
  backdrop-filter: blur(1px);
  z-index: 9998;
  display: grid;
  place-items: center;
  padding: 0 16px;

  &--show {
    left: 0;
    opacity: 1;
  }

  &__content {
    background-color: white;
    border-radius: 10px;
    padding: 15px;
    width: 100%;
    overflow-y: auto;
    max-height: calc(100% - 3.5rem);
    overflow-x: hidden;
    scrollbar-color: rgb(227, 40, 110);
    scrollbar-width: 12px;

    &::-webkit-scrollbar {
      width: 8px;
    }

    &::-webkit-scrollbar-thumb {
      background-color:  #e3286e;
      border-radius: 14px;
    }

    &::-webkit-scrollbar-track {
      background-color: #ffebf1;
      border-radius: 14px;
    }

    &__close {
      display: flex;
      flex-direction: row-reverse;

      i:hover{
        cursor: pointer;
      }
    }
  }
 }

  .close {
    color: #e3286e;
  }

</style>