<template>
  <div>
    <DeadByBingoLogo></DeadByBingoLogo>
    <BingoSheet></BingoSheet>
  </div>
</template>

<style scoped></style>

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
