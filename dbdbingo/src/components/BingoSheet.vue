<template>
  <div class="center">
    <b-row v-for="i in 5" :key="i">
        <b-col
            v-for="j in 5"
            :key="j"
            :id="i.toString() + j.toString()"
            :class="'square ' + (i.toString() + j.toString() == '33' ? 'enabled' : 'disabled')"
            @click="swapCellColor(i.toString() + j.toString())"
        >
            Row number {{i}}, Column number {{j}}
        </b-col>
    </b-row>
  </div>
</template>

<style scoped>
.center {
    margin: auto;
    width: 50%;
}
.disabled {
    background-color: rgb(64, 64, 64);
}
.enabled {
    background-color: rgb(99, 0, 0);
}
.square {
    border: 1px solid black;
    height: 0;
    width: 20%;
    padding-bottom: 20%;
    text-align: center;
}
</style>

<script>
export default {
  name: 'BingoSheet',
  methods: {
    swapCellColor(id) {
        let ele = document.getElementById(id)
        if (ele.classList.contains('disabled')) {
            ele.classList.remove('disabled')
            ele.classList.add('enabled')
        } else {
            ele.classList.remove('enabled')
            ele.classList.add('disabled')
        }
    }
  }
}
</script>
