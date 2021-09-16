<template>
  <v-container
    fluid
  >
    <div class="center">
      <v-row>
        <v-col cols="8">
          <v-card class="d-flex justify-center ">
            <v-container
              fluid
            >
              <!-- <div> -->
              <v-chip-group>
                <v-chip
                  v-for="tag in tags"
                  :key="tag"
                  color="green accent-4"
                  class="white--text"
                >
                  {{ tag }}
                </v-chip>
                <v-spacer />
                <div>
                  <v-icon class="mr-2 green--text text--accent-4">
                    mdi-table-of-contents
                  </v-icon>
                  <span
                    style="line-height: 40px;"
                    class="green--text text--accent-4"
                  >软件设计</span>
                </div>
              </v-chip-group>
              <p
                class="blue-grey--text mt-10"
              >
                <span class="mr-4 ml-3">
                  <v-icon>
                    mdi-calendar
                  </v-icon>
                  发布日期：2018-11-24
                </span>
                <span class="mr-4">
                  <v-icon>
                    mdi-file-word
                  </v-icon>
                  文章字数：8.3k
                </span>
                <span class="mr-4">
                  <v-icon>
                    mdi-clock
                  </v-icon>
                  阅读时长：9分
                </span>
                <span>
                  <v-icon>
                    mdi-eye
                  </v-icon>
                  阅读次数：2次
                </span>
              </p>
              <v-divider />
              <v-container class="px-7">
                <div
                  class="markdown-body mt-5"
                  v-html="blog"
                />
              </v-container>
            </v-container>
          </v-card>
        </v-col>
        <v-col cols="4">
          <v-card class="d-flex justify-center ">
            <v-container
              fluid
              class="pa-8"
            >
              <p
                class="text-h3 font-weight-bold blue-grey--text mb-5"
              >
                <v-icon
                  color="blue-grey"
                  class="text-h2"
                >
                  mdi-view-list-outline
                </v-icon>
                目录
              </p>
              <v-treeview
                activatable
                hoverable
                :active="active"
                :items="items"
                item-key="text"
                item-text="text"
                open-all
                open-on-click
              />
            </v-container>
          </v-card>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="8">
          <v-card class="d-flex justify-center ">
            <v-container
              fluid
            >
              <comment
                :avatar="comment.avatar"
                :placeholder="comment.placeholder"
                :comment-num="comment.commentNum"
                :author-id="comment.authorId"
                :label="comment.label"
                :comment-list="comment.commentList"
                @doSend="doSend"
                @doChidSend="doChidSend"
              />
            </v-container>
          </v-card>
        </v-col>
      </v-row>
    </div>
  </v-container>
</template>

<script>
  import marked from 'marked'
  import comment from 'hbl-comment'
  import 'github-markdown-css/github-markdown.css'
  export default {
    name: 'Article',
    components: {
      comment,
    },
    data () {
      return {
        tags: ['Java', '面向对象编程', '设计原则'],
        items: [
          { text: '特性', children: [] },
          { text: '初衷', children: [] },
          {
            text: '与 MyBatis 的 SQL 比较',
            children: [
              { text: '假设业务查询场景', children: [] },
              { text: 'MyBatis 的 SQL 写法', children: [] },
              { text: 'Fenix 的 SQL 写法', children: [] },
            ],
          },
          {
            text: 'Spring Boot 项目集成',
            children: [
              { text: 'Maven', children: [] },
              { text: '激活 Fenix FactoryBean', children: [] },
            ],
          },
        ],
        active: [
          '特性',
        ],
        blog: '',
        value: '',
        comment: {
          // 头像
          avatar: '',
          // 文本框提示内容
          placeholder: '在此输入评论内容123...',
          // 评论条数
          commentNum: 1,
          // 当前登录用户id
          authorId: 1,
          // 标签名
          label: 'LUNE',
          // 评论列表
          commentList: [
            {
              // 评论id
              id: 1,
              // 评论用户
              commentUser: {
                // 用户id
                id: 1,
                // 用户昵称
                nickName: 'LUNE',
                // 用户头像
                avatar: '',
              },
              // 被评论用户
              targetUser: { },
              // 评论内容
              content: '评论完成。。。。。。。。。。。',
              // 评论时间
              createDate: '2021-9-14 14:10:02',
              // 子评论列表
              childrenList: [],
            },
          ],
        },
      }
    },
    created () {
      const value = `
> Fenix（菲尼克斯）是一个比 MyBatis 更加强大，为解决复杂、动态 SQL (\`JPQL\`) 而生的 \`Spring Data JPA\` 扩展库，目的是辅助开发者更方便、快捷的书写复杂、动态且易于维护的 SQL，支持 \`XML\` 和 Java 链式 \`API\` 两种方式来书写动态 SQL。

 ### 特性
* 简单、轻量级、无副作用的集成和使用；
* 作为 \`JPA\` 的扩展和增强，兼容 \`Spring Data JPA\` 的各种特性；
* 提供了 \`XML\` 和纯 \`Java API\` 两种方式来书写 SQL；
* XML 的方式功能强大，让 \`SQL\` 和 \`Java\` 代码解耦，易于维护；
* 也可以采用 \`Java\` 链式 \`API\` 来书写动态 \`SQL\`；
* 具有动态性、极致的可复用性和可调试性的优点；
* 具有可扩展性，可自定义 \`XML\` 语义标签和对应的标签处理器来生成自定义逻辑的 \`SQL\` 片段和参数；

### 初衷
随着 [Spring Data JPA](https://spring.io/projects/spring-data-jpa) 越来越流行，极大的方便了数据的“增删改”和简单查询的场景，但是在复杂、动态查询方面就显得有些“糟糕”了，相比 \`MyBatis\` 的 \`XML\` 动态 \`SQL\` 而言，缺少了一定优雅和可维护性。

所以，为了能使开发人员能像在 \`MyBatis\` 中那样在 XML 中书写 \`JPQL\` 语句，\`Fenix\` 中引入了 [MVEL](http://mvel.documentnode.com/) 表达式和模板引擎的语法来书写和渲染 XML 中的动态 SQL。

因此，为了更加极致的解决 SQL 片段“**相似或重复**”的问题，Fenix 中引入了 SQL 片段的“**语义化标签**”，将大多数常见的 SQL 片段做成 \`XML\` 标签，通过传递的字段和动态的参数值就可以生成对应的 SQL 片段和命名参数。语言化的 \`XML\` 标签可以在各个需要的地方复用，也支持自定义你自己的 XML SQL 语义标签。

为了便于开发人员书写一般中短长度的动态 SQL，Fenix 还提供了 Java 链式 \`API\` 书写动态 SQL 的方式，使 SQL 可读性和紧凑性更好，如果要书写静态或动态的中、长 SQL，则推荐使用 \`XML\` 方式，便于集中阅读、调试和维护 SQL。
      `
      this.blog = marked(value)
      console.log(this.$route.params.id) // 路由带过来的值
    },
    methods: {
      // 初始文本框发送事件
      doSend (content) { // 参数：评论内容
        console.log(content)
      },
      // 评论列表中文本框发送事件
      doChidSend (content, id, parentId) { // 参数：评论内容,被评论用户id,父级评论id

      },
    },
  }
</script>

<style lang="sass" scoped>
  .center
    margin-left: 200px
    margin-right: 200px
</style>
