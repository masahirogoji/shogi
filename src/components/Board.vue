<template>
  <table>
    <tr>
      <th>9</th><th>8</th><th>7</th><th>6</th><th>5</th><th>4</th><th>3</th><th>2</th><th>1</th>
    </tr>
    <tr v-for="x in 9" :key="x" >
      <td v-for="y in 9" :key="y" >
          <img :src="pieceis[board[x-1][y-1]].img_src" @click="choicePiece(x-1,y-1)">
      </td>
      <th>{{x}}</th>
    </tr>
  </table>
</template>

<script>
import { log } from 'util';
export default {
  data() {
    return {
      pieceis: {
        0: {
          name: " ",
          img_src: require('../../assets/pieces/field.jpg')
        },
        1: {
          name: "歩",
          img_src: require('../../assets/pieces/hu_sita.jpg'),
          range: {
            x: -1,
            y: 0
          }
        },
        2: {
          name: "香",
          img_src: require('../../assets/pieces/kyou_sita.jpg')

        },
        3: {
          name: "桂",
          img_src: require('../../assets/pieces/keima_sita.jpg')

        },
        4: {
          name: "銀",
          img_src: require('../../assets/pieces/gin_sita.jpg')

        },
        5: {
          name: "金",
          img_src: require('../../assets/pieces/kin_sita.jpg')

        },
        6: {
          name: "角",
          img_src: require('../../assets/pieces/kaku_sita.jpg')

        },
        7: {
          name: "飛",
          img_src: require('../../assets/pieces/hisya_sita.jpg')

        },
        8: {
          name: "王",
          img_src: require('../../assets/pieces/ou_sita.jpg')

        },
        11: {
          name: "歩",
          img_src: require('../../assets/pieces/hu_ue.jpg')

        },
        12: {
          name: "香",
          img_src: require('../../assets/pieces/kyou_ue.jpg')

        },
        13: {
          name: "桂",
          img_src: require('../../assets/pieces/keima_ue.jpg')

        },
        14: {
          name: "銀",
          img_src: require('../../assets/pieces/gin_ue.jpg')

        },
        15: {
          name: "金",
          img_src: require('../../assets/pieces/kin_ue.jpg')

        },
        16: {
          name: "角",
          img_src: require('../../assets/pieces/kaku_ue.jpg')

        },
        17: {
          name: "飛",
          img_src: require('../../assets/pieces/hisya_ue.jpg')

        },
        18: {
          name: "王",
          img_src: require('../../assets/pieces/ou_ue.jpg')

        }

      },
      selectedPiece: 0,
      selectFlg: false,
      choicedLocation: {
        x: 0,
        y: 0
      },
      board: [
        [12,13,14,15,18,15,14,13,12],
        [0,17,0,0,0,0,0,16,0],
        [11,11,11,11,11,11,11,11,11],
        [0,0,0,0,0,0,0,0,0],
        [0,0,0,0,0,0,0,0,0],
        [0,0,0,0,0,0,0,0,0],
        [1,1,1,1,1,1,1,1,1],
        [0,6,0,0,0,0,0,7,0],
        [2,3,4,5,8,5,4,3,2]
      ]
    }
  },
  methods: {
    choicePiece(x,y) {
      if (this.selectFlg) {
        this.putPiece(x,y)
      } else {
        this.pickPiece(x,y)
      }
    },
    pickPiece(x,y) {
      if (this.board[x][y]==0) {
        return;
      }
      this.setChoicedLocation(x,y);
      this.selectedPiece = this.board[x][y]
      this.board[x].splice(y,1,0);
      this.selectFlg = true;
    },
    putPiece(x,y) {
      this.validateMove(x,y);
      this.setChoicedLocation(0,0);
      this.board[x].splice(y,1,this.selectedPiece);
      this.selectFlg = false;
    },
    validateMove(x,y) {
      if (!((x-this.choicedLocation.x == this.pieceis[this.selectedPiece].range.x) && (y-this.choicedLocation.y == this.pieceis[this.selectedPiece].range.y))) {
        alert('no');
        return
      }
    },
    setChoicedLocation(x,y) {
      this.choicedLocation.x = x;
      this.choicedLocation.y = y;
    }
  },
  computed: {
  },
}
</script>

<style scoped>
table {
  border-collapse: collapse;
}
table td {
  padding: 0px;
  border: solid 1px;
}
img{
  width: 60px;
  height: 60px;
}
</style>
