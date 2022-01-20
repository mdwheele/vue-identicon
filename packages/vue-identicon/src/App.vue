<template>
  <div>
    <Identicon seed="whack" />
    <Identicon seed="demo" />
    <Identicon seed="mdwheele" />
  </div>

  <div>
    <Identicon :seed="seed" />
    <input v-model="seed" />
  </div>
</template>

<script>
import { ref } from 'vue'
import Identicon from '@/components/Identicon.vue'

export default {
  name: 'App',
  components: { Identicon },

  setup() {
    const seed = ref(null)

    return { seed }
  }
}
</script>
