<template>
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
</template>

<script>
  export default {
    name: 'Search',
    props: {
      searchDialog: Boolean,
    },
    data () {
      return {
        screenWidth: window.screen.width - 600 + 'px',
        screenHeight: {
          height: window.screen.height - 600 + 'px',
        },
      }
    },
  }
</script>
