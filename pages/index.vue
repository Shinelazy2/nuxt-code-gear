<template>
  <div>
    <div>WelCome!</div>
    <div v-if="accessToken">{{ accessToken }}></div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  computed: {
    accessToken() {
      return this.$store.state.accessToken;
    },
  },
};
</script>
