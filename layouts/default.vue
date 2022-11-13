<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-brand href="#">Slider</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav v-if="!accessToken" class="ml-auto">
          <b-nav-item right href="/login">로그인</b-nav-item>
          <p>{{ accessToken }}</p>
        </b-navbar-nav>
        <b-nav-item @click="admin" right v-if="user.isAdmin">관리자</b-nav-item>
        <b-navbar-nav v-if="accessToken !== ''" class="ml-auto">
          <b-nav-item right @click="logout">로그아웃</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <nuxt />
  </div>
</template>
<script>
export default {
  name: 'DefaultLayout',
  computed: {
    accessToken() {
      return this.$store.state.accessToken;
    },
    user() {
      return this.$store.state.user;
    },
  },
  methods: {
    async logout() {
      await this.$store.commit('accessToken', '');
      await this.$router.push('/');
    },
    admin() {
      alert('관리자 메뉴!!!');
    },
  },
};
</script>
