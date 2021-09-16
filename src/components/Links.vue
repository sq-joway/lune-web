<template>
  <v-container>
    <v-row align="center">
      <v-col
        class="text-center"
        cols="6"
        md="auto"
      >
        <p class="white--text  mt-6 pt-md-0">
          站点总字数：1k字 | 总访问量：10次 | 总访问人数：1人
        </p>
        <p class="white--text">
          本站已安全运行3天8小时15钟20秒
        </p>
      </v-col>

      <v-spacer class="hidden-sm-and-down" />

      <v-col
        cols="12"
        md="auto"
      >
        <div class="text-body-1 font-weight-light pt-6 pt-md-0 text-center white--text mb-3">
          &copy; {{ (new Date()).getFullYear() }}, Made by <v-icon class="white--text">
            mdi-vuetify
          </v-icon>
          <a
            href="#"
            class="text-decoration-none"
          >LUNE</a>
        </div>
        <div>
          <a class="pr-8"><v-icon class="white--text">
            mdi-sina-weibo
          </v-icon></a>

          <a class="pr-8"><v-icon class="white--text">
            mdi-email
          </v-icon></a>
          <a class="pr-8"><v-icon class="white--text">
            mdi-qqchat
          </v-icon></a>
          <a><v-icon class="white--text">
            mdi-wechat
          </v-icon></a>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'Links',

    data: () => ({

    }),
  }
</script>

<style lang="sass" scoped>
  a
    color: inherit !important
</style>
