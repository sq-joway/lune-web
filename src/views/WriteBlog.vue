<template>
  <v-container>
    <v-card class="justify-center center">
      <v-form
        ref="form"
        lazy-validation
        class="ma-8"
      >
        <v-text-field
          v-model="form.title"
          label="标题"
          required
        />

        <v-text-field
          v-model="form.introduction"
          label="简介"
          required
        />

        <v-row style="z-index: 10000;">
          <v-col cols="6">
            <v-select
              v-model="form.category"
              :items="categories"
              label="分类"
              required
            />
          </v-col>
          <v-col cols="6">
            <v-select
              v-model="form.tag"
              :items="tags"
              label="标签"
              required
            />
          </v-col>
        </v-row>

        <v-row>
          <v-col cols="3">
            <v-radio-group
              v-model="form.innovation"
              label="是否原创"
              row
            >
              <v-radio
                label="原创"
                value="1"
              />
              <v-radio
                label="转载"
                value="0"
              />
            </v-radio-group>
          </v-col>
          <v-col cols="3">
            <v-radio-group
              v-model="form.type"
              label="文章类型"
              row
            >
              <v-radio
                label="博客"
                value="1"
              />
              <v-radio
                label="推广"
                value="0"
              />
            </v-radio-group>
          </v-col>
        </v-row>

        <v-text-field
          v-if="form.innovation == 0"
          v-model="form.introduction"
          label="作者"
          required
        />
        <v-text-field
          v-if="form.innovation == 0"
          v-model="form.introduction"
          label="文章出处"
          required
        />
        <v-text-field
          v-if="form.type == 0"
          v-model="form.introduction"
          label="外链"
          required
        />
        <mavon-editor
          v-model="form.content"
          style="max-height: 500px;"
        />
      </v-form>
      <v-card-actions>
        <v-spacer />
        <v-btn
          color="blue darken-1"
          class="mr-16 mb-5"
          text
        >
          <v-icon
            color="blue darken-1"
            class="pr-2"
          >
            mdi-airplane-takeoff
          </v-icon>
          发布
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-container>
</template>

<script>
  export default {
    name: 'WriteBlog',
    data () {
      return {
        form: {
          title: '',
          introduction: '',
          content: '',
          category: '',
          tag: '',
          innovation: 1,
          type: 1,
        },
        categories: ['后端开发', '前端开发', '机器学习'],
        tags: ['java', 'vue', 'linux'],
      }
    },
  }
</script>
