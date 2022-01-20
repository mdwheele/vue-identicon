<template>
  <canvas ref="el" :width="size" :height="size" />
</template>

<script>
import { ref, watchEffect } from 'vue'
import * as jdenticon from 'jdenticon'

export default {
  name: 'Identicon',

  props: {
    seed: {
      type: String,
      validator: val => val.length > 0,
      required: true
    },

    size: {
      type: Number,
      default: 256
    }
  },

  setup(props) { 
    const el = ref(null)

    jdenticon.configure({
      padding: 0
    })

    watchEffect(() => {
      if (props.seed) {
        jdenticon.update(el.value, props.seed)
      }
    })

    return {
      el
    }
  }
}
</script>
