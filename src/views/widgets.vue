<template>
  <div class="host">
    <top-host></top-host>
    <audio-host></audio-host>
    <audio-button></audio-button>
  </div>
</template>

<script>
import topHost from '../components/tabs/tabs'
import audioHost from '../components/audio/audio'
import audioButton from '../components/audio-button/audio-button'
export default {
  components: {
    topHost,
    audioHost,
    audioButton
  }
}
</script>

<style lang="scss">
.host {
  max-width: 720px;
  max-height: 540px;
  margin: 0 auto;
  border: 2px solid #C0F39C;
}
</style>
