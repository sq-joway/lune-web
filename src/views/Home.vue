<template>
  <v-container fluid>
    <v-card class="d-flex justify-center center">
      <v-container
        fluid
        class="pa-14"
      >
        <p
          class="text-h2 text-center font-weight-bold blue-grey--text"
        >
          <v-icon
            color="blue-grey"
            class="text-h2"
          >
            mdi-airballoon
          </v-icon>
          我的梦想
        </p>
        <p
          class="text-center ml-16 mr-16 grey--text text-lighten-4"
        >
          不是每个人都应该像我这样去建造一座大教堂，但是每个人都应该拥有自己的梦想，设计自己的梦想，追求自己的梦想，实现自己的梦想。梦想是生命的灵魂，是心灵的灯塔，是引导人走向成功的信仰。有了崇高的梦想，只要矢志不渝地追求，梦想就会成为现实，奋斗就会变成壮举，生命就会创造奇迹。----罗伯·舒乐
        </p>
        <p
          class="text-h2 text-center font-weight-bold blue-grey--text mt-14 mb-6"
        >
          <v-icon
            color="blue-grey"
            class="text-h2"
          >
            mdi-star-box
          </v-icon>
          推荐文章
        </p>
        <v-row>
          <v-col
            v-for="card in cards"
            :key="card.title"
            :cols="card.flex"
          >
            <v-hover
              v-slot="{ hover }"
              open-delay="200"
            >
              <v-card
                class="mx-auto"
                :elevation="hover ? 12 : 2"
                :class="{ 'on-hover' : hover}"
                max-width="374"
              >
                <v-img
                  height="250"
                  style="cursor:pointer"
                  :src="card.src"
                />

                <v-card-text>
                  <div>
                    {{ card.content }}
                  </div>
                  <div class="mt-3 text-subtitle-1">
                    <v-row>
                      <v-col cols="6">
                        <p>
                          <v-icon class="mr-1">
                            mdi-clock
                          </v-icon>
                          {{ card.time }}
                        </p>
                      </v-col>
                      <v-spacer />
                      <v-col cols="4">
                        <p class="ml-5">
                          <v-icon>mdi-bookmark</v-icon>
                          <span>{{ card.direct }}</span>
                        </p>
                      </v-col>
                    </v-row>
                  </div>
                </v-card-text>

                <v-divider class="mx-4" />

                <v-card-text>
                  <v-chip-group
                    v-model="selection"
                    active-class="deep-purple accent-4 white--text"
                    column
                  >
                    <v-chip
                      v-for="(tag,i) in card.tags"
                      :key="i"
                    >
                      {{ tag }}
                    </v-chip>
                  </v-chip-group>
                </v-card-text>

                <v-fade-transition>
                  <v-overlay
                    v-if="hover"
                    absolute
                    color="#036358"
                  >
                    <v-btn
                      rounded
                      outlined
                      color="transparent"
                      class="text-h4 brown--text text--darken-1"
                      :to="`/article/${card.title}`"
                    >
                      阅读更多
                    </v-btn>
                  </v-overlay>
                </v-fade-transition>
              </v-card>
            </v-hover>
          </v-col>
        </v-row>
        <v-pagination
          v-model="current"
          :length="pageCount"
          circle
          class="mt-8"
          :total-visible="3"
        />
      </v-container>
    </v-card>
  </v-container>
</template>

<script>
  export default {
    name: 'Home',
    data () {
      return {
        cards: [
          { title: '1', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-09-09', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4 },
          { title: '2', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-09-09', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4 },
          { title: '3', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-09-09', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4 },
          { title: '4', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-09-09', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4 },
          { title: '5', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-09-09', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4 },
          { title: '6', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-09-09', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4 },
          { title: '7', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-09-09', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4 },
          { title: '8', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-09-09', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4 },
          { title: '9', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-09-09', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4 },
        ],
        isActive: false,
        selection: 2,
        current: 1,
        pageCount: 0,
      }
    },
    created () {
      this.pageCount = this.cards.length / 9
    },
  }
</script>

<style lang="sass" scoped>
  .center
    margin-left: 300px
    margin-right: 300px
</style>
