<template>
  <v-container>
    <v-avatar
      size="150"
      class="avatar"
    >
      <v-img
        src="https://picsum.photos/510/300?random"
        aspect-ratio="1.7"
      />
    </v-avatar>
    <v-card class="d-flex justify-center center">
      <v-container
        fluid
        class="px-16"
      >
        <v-row>
          <v-col cols="4">
            <div class="post-statis">
              <div class="statis pa-5">
                <span class="count orange--text text-lighten-1 text-h4 font-weight-black text-decoration-underline">4</span>
                <span class="blue-grey--text text-lighten-4">文章</span>
              </div>
              <div class="statis pa-5">
                <span class="count orange--text text-lighten-1 text-h4 font-weight-black text-decoration-underline">6</span>
                <span class="blue-grey--text text-lighten-4">分类</span>
              </div>
              <div class="statis pa-5">
                <span class="count orange--text text-lighten-1 text-h4 font-weight-black text-decoration-underline">28</span>
                <span class="blue-grey--text text-lighten-4">标签</span>
              </div>
            </div>
          </v-col>
          <v-col cols="4" />
          <v-col cols="4">
            <div class="pt-5">
              <v-btn
                class="mr-3"
                fab
                dark
                small
                color="#FFA726"
              >
                <v-icon dark>
                  mdi-sina-weibo
                </v-icon>
              </v-btn>
              <v-btn
                class="mx-2"
                fab
                dark
                small
                color="#FFA726"
              >
                <v-icon dark>
                  mdi-email
                </v-icon>
              </v-btn>
              <v-btn
                class="mx-2"
                fab
                dark
                small
                color="#FFA726"
              >
                <v-icon dark>
                  mdi-qqchat
                </v-icon>
              </v-btn>
              <v-btn
                class="mx-2"
                fab
                dark
                small
                color="#FFA726"
              >
                <v-icon dark>
                  mdi-wechat
                </v-icon>
              </v-btn>
            </div>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            <div
              class="text-h3 text-center font-weight-black blue-grey--text text-darken-1"
            >
              LUNE
              <p class="text-h6 mt-3">
                复制工程师
              </p>
              <p class="text-h6 mt-5">
                一箪食，一瓢饮，在陋巷，人不堪其忧，不改其乐
              </p>
              <p class="text-h3 mt-16">
                <v-icon class="blue-grey--text text-darken-1">
                  mdi-tools
                </v-icon>
                我的技能
              </p>
            </div>
          </v-col>
        </v-row>
        <v-row
          v-for="(item,i) in skills"
          :key="i"
          class="mt-3"
        >
          <v-col cols="5">
            <v-progress-linear
              v-model="item.count1"
              height="25"
              :color="item.color1"
            >
              <span class="white--text ml-3">{{ item.skill1 }}</span>
              <v-divider />
              <span class="white--text mr-1">{{ item.count1 }} %</span>
            </v-progress-linear>
          </v-col>
          <v-col cols="2" />
          <v-col cols="5">
            <v-progress-linear
              v-model="item.count2"
              height="25"
              :color="item.color2"
            >
              <span class="white--text ml-3">{{ item.skill2 }}</span>
              <v-divider />
              <span class="white--text mr-1">{{ item.count2 }} %</span>
            </v-progress-linear>
          </v-col>
        </v-row>
        <v-row class="mt-3">
          <v-col cols="12">
            <p class="text-center text-h4 blue-grey--text text-darken-1">
              <v-icon class="blue-grey--text text-darken-1">
                mdi-book-open-variant
              </v-icon>
              其它技能
            </p>
            <v-chip-group
              column
              class="mx-16"
            >
              <v-chip
                v-for="(tag,i) in tags"
                :key="i"
                :color="tag.color"
                class="mx-5  my-2"
                text-color="white"
              >
                {{ tag.name }}
              </v-chip>
            </v-chip-group>
          </v-col>
        </v-row>
        <v-row class="mt-8">
          <v-col cols="12">
            <p class="text-center text-h3 blue-grey--text text-darken-1">
              <v-icon class="blue-grey--text text-darken-1">
                mdi-image
              </v-icon>
              相册
            </p>
            <v-row class="mb-5">
              <v-col
                v-for="n in 6"
                :key="n"
                class="d-flex child-flex"
                cols="4"
              >
                <v-img
                  :src="`https://picsum.photos/500/300?image=${n * 5 + 10}`"
                  :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}`"
                  aspect-ratio="1"
                  class="grey lighten-2"
                >
                  <template v-slot:placeholder>
                    <v-row
                      class="fill-height ma-0"
                      align="center"
                      justify="center"
                    >
                      <v-progress-circular
                        indeterminate
                        color="grey lighten-5"
                      />
                    </v-row>
                  </template>
                </v-img>
              </v-col>
            </v-row>
          </v-col>
        </v-row>
      </v-container>
    </v-card>
  </v-container>
</template>

<script>
  const colors = ['grey', 'blue-grey', 'brown', 'deep-orange', 'orange', 'amber', 'yellow', 'lime', 'light-green', 'green', 'teal', 'cyan', 'light-blue', 'blue', 'indigo', 'deep-purple', 'purple', 'pink', 'red']
  export default {
    name: 'About',
    data () {
      return {
        skills: [
          { skill1: 'java', count1: 90, color1: 'purple', skill2: 'javaScript', count2: 90, color2: 'blue' },
          { skill1: 'HTML', count1: 60, color1: 'teal', skill2: 'CSS', count2: 60, color2: 'green' },
          { skill1: 'SQL', count1: 80, color1: 'lime', skill2: 'VUE', count2: 70, color2: 'amber' },
        ],
        tags: [
          { name: 'C', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'Java', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'UML', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'Mybatis', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'Mybatis-plus', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'Linux', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'Markdown', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'vuetify', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'Maven', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'Google', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: '重构', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'Redis', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: '单元测试', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'Spring', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'SpringBoot', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'SpringCloud', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'Git', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'Jenkins', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'ElasticSearch', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'RabbitMQ', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'Nacos', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'Sentinel', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'Sleuth', color: colors[Math.floor((Math.random() * colors.length))] },
          { name: 'JavaFX', color: colors[Math.floor((Math.random() * colors.length))] },
        ],
      }
    },
    created () {
    },
  }
</script>

<style lang="sass" scoped>
  .avatar
    z-index: 1
    position: absolute
    top: -50px
    left: 0px
    right: 0px
    margin: 0 auto
  .post-statis
    text-align: center
    .statis
      display: inline-block
      .count
        display: block
</style>
