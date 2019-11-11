<template>
  <div id="appWhole">
    <SideBar id="appMenu" @click="mouseover" @mouseleave="mouseleave" v-bind:style="{ width: getSideMenuWidth + 'px' ,height: appSideHeight + 'px'}"/>
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
      appSideHeight: 0,
      appBodyWidth: 0,
      appBodyHeight: 0,
      hover: false
    }
  },
  computed: {
    getPageName: function () {
      let ans = this.$route.name.split('')
      ans[0] = ans[0].toUpperCase()
      return ans.join('')
    },
    getSideMenuWidth: function () {
      if (!this.hover) {
        this.getWindowWidth()
        return this.$store.state.sideBarWidth
      } else {
        return this.$store.state.sideBarWidth + 160
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
      this.appBodyWidth = this.windowWidth - this.$store.state.sideBarWidth
    },
    getWindowHeight (event) {
      this.windowHeight = document.documentElement.clientHeight
      this.appBodyHeight = this.windowHeight
      this.appSideHeight = this.windowHeight
    },
    mouseover () {
      this.hover = true
      console.log('test')
      this.getSideMenuWidth()
    },
    mouseleave () {
      this.hover = false
      console.log(this.hover)
      this.getSideMenuWidth()
    }
  }
}
</script>

<style scoped>
#appMenu {
  position: relative;
  float: left;
  background-color: #41B883;
}
#appBody {
  position: fixed;
  right: 0;
  background-color: #F7F7F8;
  overflow-y:auto;
}
</style>
