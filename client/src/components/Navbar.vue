<template>
  <div id="navbar">
    <div class="ui container secondary menu">
      <a class="header item" id="hdr" @click="goHome">Tanya-Jawab</a>
      <div class="ui category search item" id="srch" @keyup.enter.prevent="search">
        <!-- <div class="ui transparent icon input"> -->
        <div class="ui input focus" id="search">
          <input class="prompt" type="text" placeholder="Search By Title ..." v-model="keyword">
          <i class="search link icon" style="font-size: 20px;"></i>
        </div>
      </div>
      <div class="right menu">
        <div class="item">
          <div class="ui buttons" v-if="!isLogin">
            <router-link to="/login" class="ui small basic button">Login</router-link>
            <router-link to="/register" class="ui small teal button">Signup</router-link>
          </div>
            <div class="ui small basic button" v-if="isLogin" @click="logout">Logout</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  data() {
    return {
      keyword: ''
    }
  },
  computed: {
    isLogin() {
      return this.$store.state.isLogin
    }
  },
  methods: {
    logout() {
      localStorage.clear()
      this.$store.commit('setLogin', false)
    },
    search() {
      this.$store.dispatch('filterQ', '/questions?title=' + this.keyword)
    },
    goHome() {
      this.$store.dispatch('getAllQ')
      this.$router.push('/')
    }
  },
};
</script>

<style>
#navbar {
  border-top: 3px solid teal;
}
#srch {
  width: 750px;

}
#hdr {
  font-size: 1.4rem;
  font-family: 'Fredoka One', cursive;
}
#hdr:hover {
  background: transparent;
}
#search{
  display: flex;
  align-items: center;
}
</style>
