<template>
  <v-app-bar
    app
    :color="barColor"
    elevate-on-scroll
  >
    <v-row>
      <v-col cols="9" />

      <v-col
        cols="3"
        style="height: 80px;"
      >
        <div class="d-flex align-center">
          <v-img
            alt="Vuetify Logo"
            class="shrink ml-8"
            contain
            src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
            transition="scale-transition"
            width="50"
          />
        </div>
      </v-col>
    </v-row>
    <v-spacer />

    <v-btn
      text
      style="height: 60px;cursor: pointer;"
      class="mr-1 white--text text-h6"
      to="/"
    >
      <v-icon
        color="white"
        class="pr-1"
      >
        mdi-home
      </v-icon>
      首页
    </v-btn>

    <v-btn
      text
      style="height: 60px;cursor:pointer;"
      class="mr-1 white--text text-h6"
      to="/tags"
    >
      <v-icon
        color="white"
        class="pr-1"
      >
        mdi-bookmark
      </v-icon>
      标签
    </v-btn>
    <v-btn
      text
      style="height: 60px;cursor:pointer;"
      class="mr-1 white--text text-h6"
      to="/category"
    >
      <v-icon
        color="white"
        class="pr-1"
      >
        mdi-table-of-contents
      </v-icon>
      分类
    </v-btn>
    <v-btn
      text
      style="height: 60px;cursor:pointer;"
      class="mr-1 white--text text-h6"
      to="/file"
    >
      <v-icon
        color="white"
        class="pr-1"
      >
        mdi-package-variant-closed
      </v-icon>
      归档
    </v-btn>
    <v-btn
      text
      style="height: 60px;cursor:pointer;"
      class="mr-1 white--text text-h6"
      to="/about"
    >
      关于
    </v-btn>
    <v-btn
      text
      style="height: 60px;cursor:pointer;"
      class="white--text text-h6"
    >
      <v-icon
        color="white"
        class="pr-1"
        @click="search"
      >
        mdi-magnify
      </v-icon>
    </v-btn>
    <div class="ml-16">
      <v-btn
        text
        style="height: 60px;cursor:pointer;"
        class="mr-1 white--text text-h6"
        :to="writeBlog"
        @click="handleWriteBlog"
      >
        <v-icon
          color="white"
          class="pr-1"
        >
          mdi-lead-pencil
        </v-icon>
        写文章
      </v-btn>
      <v-btn
        v-if="loginShow"
        text
        style="height: 60px;cursor:pointer;"
        class="mr-1 white--text text-h6"
        @click="login"
      >
        登录
      </v-btn>
      <account v-if="accountShow" />
    </div>
    <v-spacer />
    <github-corner
      style="position: absolute; top: 0px; border: 0; right: 0;"
      :class="{'github': showFlag}"
    />
    <login
      :login-dialog="loginDialog"
      @changeLoginDialog="changeLoginDialog"
    />
    <v-dialog
      v-model="searchDialog"
      scrollable
      :max-width="screenWidth"
      style="z-index: 10001"
    >
      <v-card>
        <v-card-title>
          <v-icon class="text-h2 mr-2 blue-grey--text text-lighten-1 font-weight-black">
            mdi-search-web
          </v-icon>
          <span class="text-h3 blue-grey--text text-lighten-1 font-weight-black">搜索</span>
        </v-card-title>
        <v-card-text :style="screenHeight">
          <v-text-field
            label="请输入搜索关键字"
            required
          />
        </v-card-text>
      </v-card>
    </v-dialog>
  </v-app-bar>
</template>

<script>
  import GithubCorner from '@/components/GithubCorner'
  import Login from './widgets/Login'
  import Account from './widgets/Account'
  export default {
    name: 'AppBar',
    components: {
      GithubCorner,
      Login,
      Account,
    },
    data () {
      return {
        barColor: 'transparent',
        showFlag: true,
        writeBlog: '',
        loginDialog: false,
        loginShow: true,
        accountShow: false,
        searchDialog: false,
        screenWidth: window.screen.width - 600 + 'px',
        screenHeight: {
          height: window.screen.height - 600 + 'px',
        },
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
          this.barColor = '#32B142'
          this.showFlag = false
        } else {
          this.barColor = 'transparent'
          this.showFlag = true
        }
      },
      handleWriteBlog () {
        this.writeBlog = '/writeBlog'
        // this.openDialog = true
      },
      login () {
        this.loginDialog = true
        this.loginShow = false
        this.accountShow = true
      },
      changeLoginDialog (status) {
        this.loginDialog = status
        this.loginShow = true
        this.accountShow = false
      },
      search () {
        this.searchDialog = true
      },
    },
  }
</script>

<style lang="sass">
  .github
    display: none
</style>
