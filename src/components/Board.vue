<template>
  <table class="board">
    <tbody>
      <tr v-for="x in 9" :key="x" >
        <td v-for="y in 9" :key="y" >
          <div class="box" @click="putPiece">
            <div v-for="piece in pieceis" :key="piece.id">
              <div v-if="piece.enemyPosition.includes((y * 10) + x) || piece.myPosition.includes((y * 10) + x)">
                  <div v-if="piece.id==1">
                    <pawn></pawn>
                  </div>
                  <div v-else-if="piece.id==2">
                    香
                  </div>
                  <div v-else-if="piece.id==3">
                    桂
                  </div>
                  <div v-else-if="piece.id==4">
                    銀
                  </div>
                  <div v-else-if="piece.id==5">
                    金
                  </div>
                  <div v-else-if="piece.id==6">
                    角
                  </div>
                  <div v-else-if="piece.id==7">
                    飛
                  </div>
                  <div v-else-if="piece.id==8">
                    王
                  </div>
              </div>
            </div>
          </div>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import Pawn from "./piece/Pawn"

export default {
  components: {
    Pawn
  },
  data() {
    return {
      pieceis: {
        pawn: {
          id: 1,
          enemyPosition: [
            13, 23, 33, 43, 53, 63, 73, 83, 93
          ],
          myPosition: [
            17, 27, 37, 47, 57, 67, 77, 87, 97
          ]
        },
        lance: {
          id: 2,
          enemyPosition: [
            11, 91
          ],
          myPosition: [
            19, 99
          ]
        },
        knight: {
          id: 3,
          enemyPosition: [
            21, 81
          ],
          myPosition: [
            29, 89
          ]
        },
        silverGeneral: {
          id: 4,
          enemyPosition: [
            31, 71
          ],
          myPosition: [
            39, 79
          ]
        },
        goldGeneral: {
          id: 5,
          enemyPosition: [
            41, 61
          ],
          myPosition: [
            49, 69
          ]
        },
        bishop: {
          id: 6,
          enemyPosition: [
            82
          ],
          myPosition: [
            28
          ]
        },
        rook: {
          id: 7,
          enemyPosition: [
            22,
          ],
          myPosition: [
            88
          ]
        },
        king: {
          id: 8,
          enemyPosition: [
            51
          ],
          myPosition: [
            59
          ]
        }
      },
      board: [9][9]
    }
  },
  methods: {
    putPiece() {

    }
  },
  computed: {
  },
}
</script>

<style scoped>
.board {
  font-size: 30px;
}
.box {
  margin: 0;
  width: 60px;
  height: 60px;
  border: 1px solid black;
}
</style>
