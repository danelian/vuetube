<template>
  <div class="fixed inset-0 z-30 focus:outline-none flex justify-center items-start mx-auto" tabindex="-1" @keydown.esc="close">
    <transition 
      appear
      enter-active-class="ease-out duration-200"
      enter-from-class="opacity-0"
      enter-to-class="opacity-100"
      leave-active-class="easy-in duration-100"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
    >
      <BaseModalOverlay v-if="isOpen" @click="close" />
    </transition>
    <div v-if="isOpen" class="relative bg-white w-full sm:w-2/3 m-8">
      <div v-if="withCloseButton" class="p-2 text-right">
        <BaseModalButtonClose @click="close" />
      </div>
      <div class="p-6">
        <slot />
      </div>
      <div v-if="$slots.footer" class="flex border-t border-gray-300 py-2">
        <slot name="footer" :close="close" />
      </div>
    </div>
  </div>
</template>

<script>
import BaseModalButtonClose from './BaseModalButtonClose.vue'
import BaseModalOverlay from './BaseModalOverlay.vue'

export default {
  components: {
    BaseModalButtonClose,
    BaseModalOverlay,
  },

  props: {
    withCloseButton: Boolean
  },

  emits: ['close'],

  data () {
    return {
      isOpen: true,
      // classes: [
      //   'fixed',
      //   'inset-0',
      //   'z-30',
      //   'focus:outline-none',
      //   'flex',
      //   'justify-center',
      //   'items-start'
      // ]
    }
  },

  mounted () {
    this.$el.focus()
  },

  methods: {
    close () {
      this.isOpen = false
      
      setTimeout(() => this.$emit('close'), 100)
    }
  },

  computed: {
    classes () {
      return ['fixed inset-0 z-10 focus:outline-none']
    }
  }
}
</script>