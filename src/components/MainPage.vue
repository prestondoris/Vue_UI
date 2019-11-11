<template>
  <div id="appWhole">
    <SideBar id="appMenu" v-on:mouseover.native="mouseover" v-on:mouseleave.native="mouseleave" v-bind:style="{ width: getSideMenuWidth + 'px' ,height: appSideHeight + 'px'}"/>
    <div  id="appBody" v-bind:style="{
      width: appBodyWidth + 'px',
      height: appBodyHeight + 'px'
      }">
      <nav-bar v-bind:page=getPageName />
      <router-view/>
    </div>
  </div>
</template>

<script>
import NavBar from '@/components/NavBar.vue'
import SideBar from '@/components/SideBar.vue'

export default {
  name: 'MainPage',
  components: {
    NavBar,
    SideBar
  },
  data: function () {
    return {
      windowWidth: 0,
      windowHeight: 0,
      appSideWidth: this.$store.state.sideBarWidth,
      appSideHeight: 0,
      appBodyWidth: 0,
      appBodyHeight: 0
    }
  },
  computed: {
    getPageName: function () {
      let ans = this.$route.name.split('')
      ans[0] = ans[0].toUpperCase()
      return ans.join('')
    },
    getSideMenuWidth: {
      get: function () {
        if (this.$store.state.sideCollapsedHover) {
          return this.appSideWidth
        } else {
          this.getWindowWidth()
          return this.appSideWidth
        }
      },
      set: function (value) {
        this.appSideWidth = value
      }
    }
  },
  beforeMount () {
    this.getWindowWidth()
    this.getWindowHeight()
  },
  mounted () {
    this.$nextTick(function () {
      window.addEventListener('resize', this.getWindowWidth)
      window.addEventListener('resize', this.getWindowHeight)
    })
  },
  methods: {
    getWindowWidth (event) {
      this.windowWidth = document.documentElement.clientWidth
      this.appSideWidth = this.$store.state.sideBarWidth
      this.appBodyWidth = this.windowWidth - this.appSideWidth
    },
    getWindowHeight (event) {
      this.windowHeight = document.documentElement.clientHeight
      this.appBodyHeight = this.windowHeight
      this.appSideHeight = this.windowHeight
    },
    mouseover () {
      this.$store.state.sideCollapsedHover = true
      if (this.$store.state.sideCollapsed) {
        this.getSideMenuWidth = this.$store.state.sideBarWidth + 160
      }
    },
    mouseleave () {
      this.$store.state.sideCollapsedHover = false
      if (this.$store.state.sideCollapsed) {
        this.getSideMenuWidth = this.$store.state.sideBarWidth
      }
    }
  }
}
</script>

<style scoped>
#appMenu {
  position: relative;
  float: left;
  background-color: #41B883;
  z-index: 100;
}
#appBody {
  position: fixed;
  right: 0;
  background-color: #F7F7F8;
  overflow-y:auto;
}
</style>
