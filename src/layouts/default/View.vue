<template>
  <v-main>
    <v-container fluid>
      <router-view :key="$router.path" />
    </v-container>
  </v-main>
</template>

<script>
  export default {
    mame: 'DefaultView',
  }
</script>
