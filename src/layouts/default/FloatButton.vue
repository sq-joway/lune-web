<template>
  <v-container
    class="fab"
    style="scroll-behavior: smooth;"
  >
    <v-fab-transition>
      <v-btn
        v-show="iftop"
        key="mdi-share-variant"
        color="red"
        fab
        large
        dark
        bottom
        right
        absolute
        class="v-btn--example pbtn"
        @click="toTop"
      >
        <v-icon>mdi-arrow-up</v-icon>
      </v-btn>
    </v-fab-transition>
  </v-container>
</template>

<script>
  export default {
    name: 'FloatButton',
    data () {
      return {
        iftop: false,
      }
    },
    /** 滚动条监听 */
    created () { this.listenerFunction() },
    beforeDestroy () {
      document.removeEventListener('scroll', this.listenerFunction)
    },
    methods: {
      listenerFunction (e) {
        document.addEventListener('scroll', this.handleScroll, true)
      },
      handleScroll () {
        const scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop
        if (scrollTop) {
          this.iftop = true
        } else {
          this.iftop = false
        }
      },
      // 锚点回到顶部
      toTop () {
        window.scrollTo(0, 0)
      },
    },
  }
</script>

<style>
  .fab {
    position: fixed;
    bottom: 100px;
    right: 50px;
    z-index: 500;
  }
</style>
