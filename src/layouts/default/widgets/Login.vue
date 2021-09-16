<template>
  <v-dialog
    v-model="loginDialog"
    persistent
    max-width="400px"
    style="z-index: 10001;"
  >
    <v-card>
      <v-card-title
        class="text-center"
        style="display: block;"
      >
        <span class="text-h4 blue-grey--text text-lighten-1 font-weight-black">登 录</span>
      </v-card-title>
      <v-card-text>
        <v-container>
          <v-row>
            <v-col cols="12">
              <v-text-field
                label="用户名"
                required
              />
            </v-col>
            <v-col cols="12">
              <v-text-field
                label="密码"
                type="password"
                required
              />
            </v-col>
          </v-row>
        </v-container>
      </v-card-text>
      <v-card-actions>
        <div class="mr-6">
          <v-btn
            depressed
            width="100"
            class="grey--text text-lighten-4 mx-13"
            @click="submit"
          >
            登录
          </v-btn>
          <v-btn
            depressed
            width="100"
            class="grey--text text-lighten-4"
            @click="cancle"
          >
            取消
          </v-btn>
        </div>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
  export default {
    name: 'Login',
    props: {
      loginDialog: Boolean,
    },
    data () {
      return {

      }
    },
    methods: {
      submit () {},
      cancle () {
        this.$emit('changeLoginDialog', false)
      },
    },
  }
</script>
