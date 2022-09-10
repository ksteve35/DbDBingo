<template>
  <div class="app-font-color">
    <DeadByBingoLogo></DeadByBingoLogo>
    <BingoSheet></BingoSheet>
  </div>
</template>

<style scoped>
.app-font-color {
  color: rgb(231, 231, 231)
}
</style>

<script>
import BingoSheet from './components/BingoSheet.vue'
import DeadByBingoLogo from './components/DeadByBingoLogo.vue'
export default {
  name: 'App',
  components: {
    BingoSheet,
    DeadByBingoLogo
  }
}
</script>
