<template>
  <v-carousel
    hide-delimiters
    app
  >
    <v-carousel-item
      v-for="(item,i) in items"
      :key="i"
      :src="item.src"
    >
      <v-overlay
        color="pink"
        absolute
      >
        <div style="margin-top: 200px;">
          <p
            class="text-h1 text-center"
          >
            Vue 文档风格的 Typora 主题
          </p>

          <p
            class="text-center text-h4"
            style="margin-bottom: 80px; width: 800px;"
          >
            typora-vue-theme 是 Typora Markdown 文档编辑器中一款类似Vue文档风格的主题。 简介Typora是一款支持实时预览的 Markdown 编辑器和阅读器，支持Windows、macOS、Linux三大平台
          </p>

          <v-hover
            v-slot="{ hover }"
          >
            <v-btn
              color="white"
              rounded
              outlined
              width="200"
              height="50"
              :style="{ 'backgroundColor': hover ? '#EF5350' : 'transparent' }"
              style="display: block; margin: 0 auto;"
              @click="overlay = false"
            >
              <span class="text-h4">阅读更多</span>
            </v-btn>
          </v-hover>
        </div>
      </v-overlay>
    </v-carousel-item>
  </v-carousel>
</template>

<script>

  export default {
    name: 'Carousel',
    data () {
      return {
        carouselHeight: window.screen.height,
        items: [
          { src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png' },
          { src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png' },
          { src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png' },
          { src: 'http://static.blinkfox.com/blog/2019/08/20jpa-20190820.png' },
        ],
      }
    },

  }
</script>

<style>
</style>
