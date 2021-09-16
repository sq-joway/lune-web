<template>
  <v-container fluid>
    <v-card class="d-flex justify-center center">
      <v-container
        fluid
        class="pa-14"
      >
        <p
          class="text-h2 text-center font-weight-bold blue-grey--text mb-5"
        >
          <v-icon
            color="blue-grey"
            class="text-h2"
          >
            mdi-file-tree
          </v-icon>
          文章归档
        </p>
        <div
          id="treeChart"
          :style="{'width': '600px', 'height': '400px'}"
          style="margin: 0 auto"
        />
      </v-container>
    </v-card>
    <v-card class="d-flex justify-center center mt-5">
      <v-container
        fluid
        class="pa-14"
      >
        <v-timeline
          align-top
          :dense="$vuetify.breakpoint.smAndDown"
        >
          <v-timeline-item
            v-for="(item, i) in items"
            :key="i"
            :icon="item.icon"
            fill-dot
          >
            <span
              slot="opposite"
              class="indigo--text text-h4 font-weight-bold"
            ><v-icon class="mr-1 indigo--text text-h3">
              mdi-clock
            </v-icon>{{ item.time }}</span>
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
                  :src="item.src"
                />

                <v-card-text>
                  <div>
                    {{ item.content }}
                  </div>
                  <div class="mt-3 text-subtitle-1">
                    <v-row>
                      <v-col cols="6">
                        <p>
                          <v-icon class="mr-1">
                            mdi-clock
                          </v-icon>
                          {{ item.time }}
                        </p>
                      </v-col>
                      <v-spacer />
                      <v-col cols="4">
                        <p class="ml-5">
                          <v-icon>mdi-bookmark</v-icon>
                          <span>{{ item.direct }}</span>
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
                      v-for="(tag, index) in item.tags"
                      :key="index"
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
                      :to="`/article/${item.title}`"
                    >
                      阅读更多
                    </v-btn>
                  </v-overlay>
                </v-fade-transition>
              </v-card>
            </v-hover>
          </v-timeline-item>
        </v-timeline>
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
    name: 'Tags',
    data () {
      return {
        items: [
          { title: '1', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-09-09', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4, icon: 'mdi-star' },
          { title: '2', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-08-20', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4, icon: 'mdi-book-variant' },
          { title: '3', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-07-13', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4, icon: 'mdi-airballoon' },
          { title: '4', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-06-10', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4, icon: 'mdi-buffer' },
          { title: '5', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-05-02', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4, icon: 'mdi-buffer' },
          { title: '6', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-04-10', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4, icon: 'mdi-buffer' },
          { title: '7', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-03-16', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4, icon: 'mdi-buffer' },
          { title: '8', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-02-01', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4, icon: 'mdi-buffer' },
          { title: '9', content: '一个 bug 被隐藏的时间越长，修复这个 bug 的代价就越大。 我曾经在 单元测试指南 一文中写到过单元测试的必要性和 Java 单元测试相关', time: '2021-01-18', direct: '后端', tags: ['Java', 'Spring', 'Redis'], src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png', flex: 4, icon: 'mdi-buffer' },
        ],
        selection: '',
        current: 1,
        pageCount: 2,
        treeData: [
          {
            name: '文档',
            children: [
              {
                name: '2021年',
                children: [
                  {
                    name: '1月',
                    children: [
                      { name: '1篇' },
                    ],
                  },
                  {
                    name: '2月',
                    children: [
                      { name: '2篇' },
                    ],
                  },
                  {
                    name: '3月',
                    children: [
                      { name: '1篇' },
                    ],
                  },
                  {
                    name: '4月',
                    children: [
                      { name: '2篇' },
                    ],
                  },
                  {
                    name: '5月',
                    children: [
                      { name: '1篇' },
                    ],
                  },
                  {
                    name: '6月',
                    children: [
                      { name: '2篇' },
                    ],
                  },
                  {
                    name: '7月',
                    children: [
                      { name: '1篇' },
                    ],
                  },
                  {
                    name: '8月',
                    children: [
                      { name: '2篇' },
                    ],
                  },
                  {
                    name: '9月',
                    children: [
                      { name: '1篇' },
                    ],
                  },
                  {
                    name: '10月',
                    children: [
                      { name: '2篇' },
                    ],
                  },
                  {
                    name: '11月',
                    children: [
                      { name: '1篇' },
                    ],
                  },
                  {
                    name: '12月',
                    children: [
                      { name: '1篇' },
                    ],
                  },
                ],
              },
              {
                name: '2020年',
                children: [
                  {
                    name: '1月',
                    children: [
                      { name: '1篇' },
                    ],
                  },
                  {
                    name: '2月',
                    children: [
                      { name: '2篇' },
                    ],
                  },
                  {
                    name: '3月',
                    children: [
                      { name: '1篇' },
                    ],
                  },
                  {
                    name: '4月',
                    children: [
                      { name: '2篇' },
                    ],
                  },
                  {
                    name: '5月',
                    children: [
                      { name: '1篇' },
                    ],
                  },
                  {
                    name: '6月',
                    children: [
                      { name: '2篇' },
                    ],
                  },
                  {
                    name: '7月',
                    children: [
                      { name: '1篇' },
                    ],
                  },
                  {
                    name: '8月',
                    children: [
                      { name: '2篇' },
                    ],
                  },
                  {
                    name: '9月',
                    children: [
                      { name: '1篇' },
                    ],
                  },
                  {
                    name: '10月',
                    children: [
                      { name: '2篇' },
                    ],
                  },
                  {
                    name: '11月',
                    children: [
                      { name: '1篇' },
                    ],
                  },
                  {
                    name: '12月',
                    children: [
                      { name: '1篇' },
                    ],
                  },
                ],
              },
            ],
          },
        ],
      }
    },
    mounted () {
      this.drawTreeChart()
    },
    methods: {
      clickTagItem (tag) {
        console.log(tag)
      },
      drawTreeChart () {
        const mychart = this.$echarts.init(document.getElementById('treeChart'))
        const option = {
          series: [
            {
              type: 'tree',
              data: this.treeData,
              top: '1%',
              left: '7%',
              bottom: '1%',
              right: '20%',
              symbolSize: 7,
              label: {
                position: 'left',
                verticalAlign: 'middle',
                align: 'right',
                fontSize: 9,
              },
              leaves: {
                label: {
                  position: 'right',
                  verticalAlign: 'middle',
                  align: 'left',
                },
              },

              emphasis: {
                focus: 'descendant',
              },

              expandAndCollapse: true,
              animationDuration: 550,
              animationDurationUpdate: 750,
            },
          ],
        }
        mychart.setOption(option)
      },
    },
  }
</script>

<style lang="sass" scoped>
  .center
    margin-left: 300px
    margin-right: 300px
</style>
