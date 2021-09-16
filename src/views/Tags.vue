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
            mdi-label-multiple
          </v-icon>
          文章标签
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
        <tag-cloud
          :data="tags"
          style="cursor:pointer"
          :config="cloudConfig"
          @clickTag="clickTagItem"
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
          { name: 'Hexo', color: colors[Math.floor((Math.random() * colors.length))], value: 1 },
          { name: 'PostgreSQL', color: colors[Math.floor((Math.random() * colors.length))], value: 3 },
          { name: '数据库', color: colors[Math.floor((Math.random() * colors.length))], value: 2 },
          { name: 'Java', color: colors[Math.floor((Math.random() * colors.length))], value: 4 },
          { name: '面向对象编程', color: colors[Math.floor((Math.random() * colors.length))], value: 2 },
          { name: 'CPU缓存', color: colors[Math.floor((Math.random() * colors.length))], value: 2 },
          { name: 'UML', color: colors[Math.floor((Math.random() * colors.length))], value: 3 },
          { name: '性能测试', color: colors[Math.floor((Math.random() * colors.length))], value: 1 },
          { name: 'HVEL', color: colors[Math.floor((Math.random() * colors.length))], value: 2 },
          { name: 'JPA', color: colors[Math.floor((Math.random() * colors.length))], value: 10 },
          { name: 'Fenix', color: colors[Math.floor((Math.random() * colors.length))], value: 5 },
          { name: 'Linux', color: colors[Math.floor((Math.random() * colors.length))], value: 6 },
          { name: 'Typora', color: colors[Math.floor((Math.random() * colors.length))], value: 3 },
          { name: 'Markdown', color: colors[Math.floor((Math.random() * colors.length))], value: 2 },
          { name: 'Vue', color: colors[Math.floor((Math.random() * colors.length))], value: 4 },
          { name: '设计模式', color: colors[Math.floor((Math.random() * colors.length))], value: 6 },
          { name: 'Apache', color: colors[Math.floor((Math.random() * colors.length))], value: 8 },
          { name: 'Google', color: colors[Math.floor((Math.random() * colors.length))], value: 2 },
          { name: '重构', color: colors[Math.floor((Math.random() * colors.length))], value: 2 },
          { name: '测试', color: colors[Math.floor((Math.random() * colors.length))], value: 3 },
          { name: '设计原则', color: colors[Math.floor((Math.random() * colors.length))], value: 5 },
          { name: '单元测试', color: colors[Math.floor((Math.random() * colors.length))], value: 11 },
          { name: 'Spring', color: colors[Math.floor((Math.random() * colors.length))], value: 5 },
          { name: 'SpringBoot', color: colors[Math.floor((Math.random() * colors.length))], value: 7 },
          { name: 'SpringCloud', color: colors[Math.floor((Math.random() * colors.length))], value: 5 },
          { name: 'Git', color: colors[Math.floor((Math.random() * colors.length))], value: 3 },
          { name: 'Jenkins', color: colors[Math.floor((Math.random() * colors.length))], value: 2 },
          { name: 'GitLab', color: colors[Math.floor((Math.random() * colors.length))], value: 4 },
        ],
        selection: '',
        cloudConfig: {
          radius: 180,
          hover: false,
        },
      }
    },
    created () {
    },
    methods: {
      clickTagItem (tag) {
        console.log(tag)
      },
    },
  }
</script>

<style lang="sass" scoped>
  .center
    margin-left: 300px
    margin-right: 300px
</style>
