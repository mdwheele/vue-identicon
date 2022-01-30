<template>
  <canvas v-if="theme === 'geometric'" ref="el" :width="size" :height="size" />
  <img v-else-if="theme === 'retro'" ref="el" :width="size" :height="size" src="" />
</template>

<script>
import { ref, watchEffect } from 'vue'
import * as jdenticon from 'jdenticon'
import Identicon from 'identicon.js'
import md5 from 'md5'

export default {
  name: 'Identicon',

  props: {
    seed: {
      type: String,
      validator: val => val.length > 0,
      required: true
    },

    theme: {
      type: String,
      validator: val => ['geometric', 'retro'].includes(val),
      default: 'geometric'
    },

    size: {
      type: Number,
      default: 256
    }
  },

  setup(props) { 
    const el = ref(null)

    watchEffect(() => {
      if (props.theme === 'geometric') {
        jdenticon.configure({
          padding: 0
        })

        jdenticon.update(el.value, props.seed)
      } else if (props.theme === 'retro') {
        const data = new Identicon(md5(props.seed), { 
          background: [255, 255, 255, 255],
          margin: 0,
          size: props.size
        }).toString()

        if (el.value) {
          el.value.src = `data:image/png;base64,${data}`
        }
      }
    })

    return {
      el
    }
  }
}
</script>
