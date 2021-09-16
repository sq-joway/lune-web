<template>
  <div>
    <v-app>
      <default-bar />
      <default-carousel />
      <default-view />
      <default-footer />
      <default-music />
      <default-flaot-button />
      <background ref="background" />
    </v-app>
  </div>
</template>

<script>
  import Background from '@/components/Background'
  export default {
    name: 'DefaultLayout',

    components: {
      DefaultBar: () => import(
        /* webpackChunkName: "default-app-bar" */
        './AppBar'
      ),
      DefaultCarousel: () => import(
        /* webpackChunkName: "default-app-bar" */
        './Carousel'
      ),
      DefaultFooter: () => import(
        /* webpackChunkName: "default-footer" */
        './Footer'
      ),
      DefaultView: () => import(
        /* webpackChunkName: "default-view" */
        './View'
      ),
      DefaultMusic: () => import(
        /* webpackChunkName: "default-view" */
        './Music'
      ),
      DefaultFlaotButton: () => import(
        /* webpackChunkName: "default-view" */
        './FloatButton'
      ),
      Background,
    },
    methods: {
      createLoves () {
        this.$refs.background.createLoves(event)
      },
      removeSmallHert () {
        this.$refs.background.removeSmallHert()
      },
    },
  }
</script>
