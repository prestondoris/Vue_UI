<template>
  <div id="appWhole">
    <SideBar id="appMenu" />
    <div id="appBody" v-bind:style="{
      width: appBodyWidth + 'px',
      height: appBodyHeight + 'px'
      }">
      <NavBar />
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
      msg: 'Hello World! This is a Event listener test.',
      windowWidth: 0,
      windowHeight: 0,
      appSideWidth: 250,
      appBodyWidth: 0,
      appBodyHeight: 0
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
      this.appBodyWidth = this.windowWidth - this.appSideWidth
    },
    getWindowHeight (event) {
      this.windowHeight = document.documentElement.clientHeight
      this.appBodyHeight = this.windowHeight
    }
  }
}
</script>

<style scoped>
  #appMenu {
    width: 250px;
    position: fixed;
    float: left;
    border: solid black 1px;
    height: 100%;
    background-color: #41B581;
  }

  #appBody {
    position: fixed;
    right: 0;
    background-color: #F7F7F8;
    overflow-y:auto;
  }
</style>
