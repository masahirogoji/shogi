<template>
  <div>
    <slot name="pieces" :pieceName="pieceName" :enemyPosition="enemyPosition" :myPosition="myPosition">
    </slot>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pieceName: '歩',
      enemyPosition: [
        '1-3','2-3','3-3','4-3','5-3','6-3','7-3','8-3','9-3'
      ],
      myPosition: [
        '1-7','2-7','3-7','4-7','5-7','6-7','7-7','8-7','9-7'
      ]

    }
  },
}
</script>

<style>

</style>
