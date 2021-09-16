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
            mdi-drag
          </v-icon>
          文章分类
        </p>
        <!-- <v-row>
          <v-col

            :cols="2"
          > -->
        <v-chip-group
          v-model="selection"
          active-class="deep-purple accent-4 black--text"
          column
        >
          <v-chip
            v-for="(tag, i) in tags"
            :key="i"
            class="ma-4"
            :color="tag.color"
            text-color="white"
          >
            {{ tag.name }}<span class="black--text ml-3">{{ tag.value }}</span>
          </v-chip>
        </v-chip-group>
        <!-- </v-col> -->
        <!-- </v-row> -->
      </v-container>
    </v-card>
    <v-card class="d-flex justify-center center mt-5">
      <v-container
        fluid
        class="pa-14"
      >
        <div
          id="radar"
          :style="{'width': '800px', 'height': '400px'}"
          style="margin: 0 auto"
        />
      </v-container>
    </v-card>
  </v-container>
</template>

<script>
  const colors = ['grey', 'blue-grey', 'brown', 'deep-orange', 'orange', 'amber', 'yellow', 'lime', 'light-green', 'green', 'teal', 'cyan', 'light-blue', 'blue', 'indigo', 'deep-purple', 'purple', 'pink', 'red']
  export default {
    name: 'Tags',
    data () {
      return {
        tags: [
          { name: '前端', color: colors[Math.floor((Math.random() * colors.length))], value: 3 },
          { name: '数据库', color: colors[Math.floor((Math.random() * colors.length))], value: 5 },
          { name: '编程之道', color: colors[Math.floor((Math.random() * colors.length))], value: 8 },
          { name: '软件工具', color: colors[Math.floor((Math.random() * colors.length))], value: 4 },
          { name: '软件设计', color: colors[Math.floor((Math.random() * colors.length))], value: 2 },
          { name: '后端', color: colors[Math.floor((Math.random() * colors.length))], value: 9 },
        ],
        selection: '',
        cloudConfig: {
          radius: 180,
          hover: false,
        },
      }
    },
    mounted () {
      this.drawChart()
    },
    methods: {
      clickTagItem (tag) {
        console.log(tag)
      },
      drawChart () {
        // 基于准备好的dom，初始化echarts实例
        const myChart = this.$echarts.init(document.getElementById('radar'))

        const option = {
          title: {
            text: '文章分类图',
          },
          legend: {
            data: ['文章分类'],
          },
          radar: {
            // shape: 'circle',
            indicator: [
              { name: '前端', max: 10 },
              { name: '数据库', max: 10 },
              { name: '编程之道', max: 10 },
              { name: '软件工具', max: 10 },
              { name: '软件设计', max: 10 },
              { name: '后端', max: 10 },
            ],
          },
          series: [{
            name: '文章分类',
            type: 'radar',
            data: [
              {
                value: [2, 5, 8, 4, 2, 9],
                name: '文章分类',
              },
            ],
          }],
        }
        // 绘制图表
        myChart.setOption(option)
      },
    },
  }
</script>

<style lang="sass" scoped>
  .center
    margin-left: 300px
    margin-right: 300px
</style>
