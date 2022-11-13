<template>
  <a @click="loginWithKakao">
    <img src="/images/kakao_login.png" />
  </a>
</template>

<script>
// const Kakao = window.client.KaKao;
export default {
  name: 'LoginPage',
  mounted() {
    this.kakaoInit();
  },
  methods: {
    kakaoInit() {
      window.Kakao.init('510d288640e131f7b1d04ddef2168bd2'); // KaKao client key
      window.Kakao.isInitialized();
    },
    async loginWithKakao() {
      await window.Kakao.Auth.authorize({
        redirectUri: `${window.location.origin}/kakao-callback`,
      });
    },
  },
};
</script>
