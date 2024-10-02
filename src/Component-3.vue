<script lang="ts" setup>
import { ref } from 'vue'

const toto = ref(false)
</script>

<template>
  <div
    id="tabpanel-406-panel"
    class="fr-tabs__panel fr-tabs__panel--selected"
    role="tabpanel"
    aria-labelledby="tabpanel-406"
    tabindex="0"
  >
    <p>Contenu 3</p>
    <button @click="toto = !toto">coucou</button>
    <div v-if="toto">
      dwadawdawdawda<br />
      dadawdawwda<br />
      adawdwadawdawd<br />
      dadwwaddwawdad<br />
      dadawdwadawd<br />
      dawdawdawd<br />
    </div>
  </div>
</template>
