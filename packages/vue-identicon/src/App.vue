<template>
  <h1>Default Theme</h1>
  <div>
    <Identicon seed="whack" />
    <Identicon seed="demo" />
    <Identicon seed="mdwheele" />
  </div>

  <h1>Retro Theme</h1>
  <div>
    <Identicon seed="whack" theme="retro" />
    <Identicon seed="demo" theme="retro" />
    <Identicon seed="mdwheele" theme="retro" />
  </div>

  <h1>Playground</h1>
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
