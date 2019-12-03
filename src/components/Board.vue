<template>
  <div class="board">
    <div v-for="x in 9" :key="x" >
      <div v-for="y in 9" :key="y" >
        <div class="box">

          <foot-soldier>
            <template v-slot:pieces="pieces">
              {{ pieces.pieceName }}
            </template>
          </foot-soldier>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import footSoldier from "./piece/footSoldier"

export default {
  components: {
    footSoldier
  },
  data() {
    return {
      board: [
        ["香","桂","銀","金","王","金","銀","桂","香"],
        ["　","角","　","　","　","　","　","飛","　"],
        ["歩","歩","歩","歩","歩","歩","歩","歩","歩"],
        ["　","　","　","　","　","　","　","　","　"],
        ["　","　","　","　","　","　","　","　","　"],
        ["　","　","　","　","　","　","　","　","　"],
        ["歩","歩","歩","歩","歩","歩","歩","歩","歩"],
        ["　","角","　","　","　","　","　","飛","　"],
        ["香","桂","銀","金","王","金","銀","桂","香"]
      ],
      choicedBoard: ""
    }
  },
  methods: {
  },
  computed: {
  },
}
</script>

<style scoped>
.board {
  display: grid;
  grid-template-rows: repeat(9, 1fr);
  grid-template-columns: repeat(9, 1fr);
}
.box {
  border: 1px solid black;
}
</style>
