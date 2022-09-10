<template>
  <b-img :src="DeadByBingoImg" class="center-img"></b-img>
</template>

<style scoped>
.center-img {
    display: block;
    height: auto;
    margin-left: auto;
    margin-right: auto;
    width: auto;
    max-width: 20%;
    padding: 1% 0px 1% 0px;
}
</style>

<script>
import DeadByBingo from '../assets/DeadByBingo.png'
export default {
  name: 'DeadByBingoLogo',
  data() {
    return {
      DeadByBingoImg: DeadByBingo
    }
  }
}
</script>
