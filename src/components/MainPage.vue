<template>
  <div id="appWhole">
    <SideBar id="appMenu"  v-bind:style="{ height: appSideHeight + 'px'}"/>
    <div  id="appBody" v-bind:style="{
      width: appBodyWidth + 'px',
      height: appBodyHeight + 'px'
      }">
      <nav-bar v-bind:page=$route.name />
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
      appSideWidth: 250,
      appSideHeight: 0,
      appBodyWidth: 0,
      appBodyHeight: 0
    }
  },
  // computed: {
  //   getPageName: function() {
  //     this.$route
  //   }
  // },
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
      this.appBodyWidth = this.windowWidth - this.appSideWidth
    },
    getWindowHeight (event) {
      this.windowHeight = document.documentElement.clientHeight
      this.appBodyHeight = this.windowHeight
      this.appSideHeight = this.windowHeight
    },
    setSideMenuWidth (value) {
      console.log(value)
      this.appSideWidth = value
    }
  }
}
</script>

<style scoped>
  #appMenu {
    width: 250px;
    position: relative;
    float: left;
    height: 100%;
    background-color: #41B883;
  }

  #appBody {
    position: fixed;
    right: 0;
    background-color: #F7F7F8;
    overflow-y:auto;
  }
</style>
