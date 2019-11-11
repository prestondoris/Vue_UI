<template>
  <b-nav vertical>
    <b-nav-text tag="div" id="logoName">
      <img src="@/assets/fuge.png" alt="logo">
      <span><h3>Fugeware</h3></span>
    </b-nav-text>
    <Divider />
    <b-nav-text id="user" tag="div"><i class="fas fa-user-cog"></i><span><h4>Preston Doris</h4></span></b-nav-text>
    <Divider />
    <b-nav-item><router-link class="nav-link" to="/">Home</router-link></b-nav-item>
    <b-nav-item><router-link class="nav-link" to="/about">About</router-link></b-nav-item>
    <b-nav-item disabled>Disabled</b-nav-item>
  </b-nav>
</template>

<script>
import Divider from '@/components/Divider.vue'
export default {
  name: 'SideBar',
  components: {
    Divider
  }
}
</script>

<style scoped>
#logoName {
    font-size: 1.5em;
    width: 100%;
    margin-left: auto;
    margin-right: auto;
    display: inline;
}

#logoName span img {
    display: inline;
}

#user i span {
  display: inline;
}

img {
  width: 50px;
}

b-nav {
  width: 100%;
  background-color: white;
}
</style>
