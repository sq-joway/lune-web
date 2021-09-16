<template>
  <v-container class="palyer">
    <player />
  </v-container>
</template>

<script>
  import Player from 'zw-player'
  export default {
    name: 'Music',
    components: {
      Player,
    },
  }
</script>

<style scoped>
.palyer {
  position: fixed;
  top: 0px;
  right: 560px;
  z-index: 500;
}
</style>
