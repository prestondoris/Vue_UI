<template>
  <b-nav vertical>
    <b-nav-text id="logoName" >
      <div class="nav-link">
        <img src="@/assets/fuge.png" alt="logo">
        <h3 v-bind:class="[$store.state.sideCollapsed  && !$store.state.sideCollapsedHover ? activeClass : fwLink]">Fugeware</h3>
      </div>
    </b-nav-text>
    <Divider />
    <b-nav-text class="b-nav-item b-nav-text">
        <div class="nav-link">
          <i class="fas fa-user-cog icon"></i>
          <h4 v-bind:class="[$store.state.sideCollapsed  && !$store.state.sideCollapsedHover ? activeClass : fwLink]">Preston Doris</h4>
        </div>
    </b-nav-text>
    <Divider />
    <b-nav-item class="b-nav-item b-nav">
      <router-link class="nav-link " to="/">
        <i class="fas fa-chart-pie icon"></i>
        <h5 v-bind:class="[$store.state.sideCollapsed  && !$store.state.sideCollapsedHover ? activeClass : fwLink]">Dashboard</h5>
      </router-link>
    </b-nav-item>
    <b-nav-item class="b-nav-item b-nav">
      <router-link class="nav-link" to="/brands">
        <i class="fas fa-briefcase icon"></i>
        <h5 v-bind:class="[$store.state.sideCollapsed && !$store.state.sideCollapsedHover ? activeClass : fwLink]">Brands</h5>
      </router-link>
    </b-nav-item>
    <b-nav-item class="b-nav-item b-nav">
      <router-link class="nav-link" to="/fermentations">
        <i class="fas fa-chart-area icon"></i>
        <h5 v-bind:class="[$store.state.sideCollapsed  && !$store.state.sideCollapsedHover ? activeClass : fwLink]">Fermentations</h5>
      </router-link>
    </b-nav-item>
    <b-nav-item class="b-nav-item b-nav">
      <router-link class="nav-link" to="/brew">
        <i class="fas fa-beer icon"></i>
        <h5 v-bind:class="[$store.state.sideCollapsed  && !$store.state.sideCollapsedHover ? activeClass : fwLink]">Brew</h5>
      </router-link>
    </b-nav-item>
    <b-nav-item class="b-nav-item b-nav">
      <router-link class="nav-link" to="/batches">
        <i class="fas fa-clipboard-list icon"></i>
        <h5 v-bind:class="[$store.state.sideCollapsed  && !$store.state.sideCollapsedHover ? activeClass : fwLink]">Batches</h5>
      </router-link>
    </b-nav-item>
  </b-nav>
</template>

<script>
import Divider from '@/components/Divider.vue'
export default {
  name: 'SideBar',
  data: function () {
    return {
      activeClass: 'active',
      fwLink: 'fw-link'
    }
  },
  components: {
    Divider
  }
}
</script>

<style scoped>
#logoName {
    font-size: 1.5em;
    width: 100%;
    text-align: left;
}
img {
  vertical-align: middle;
  display: inline-block;
  width: 50px;
}
.b-nav-text {
  padding-left: 1em;
}
.b-nav-item {
  margin: .5em 0 .5em 0;
  text-align: left;
  width: 100%;
}
.active {
  display: none;
}
.b-nav:hover {
  background-color: white;
  border-radius: 5px;
  opacity: 1;
  background: hsla(0,0%,100%,.23)
}
.fw-link {
  padding: 0 0 0 .5em;
  margin:0;
  vertical-align: middle;
  display: inline-block;
}
.nav-link {
  color: #2C3E50;
}
.icon {
  vertical-align: middle;
  display: inline-block;
}
</style>
