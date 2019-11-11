<template>
  <nav id="navbar" class="navbar navbar-expand-lg navbar-light">
    <b-button id="collapseSideBtn" class="fw-button" v-on:click="collapseSideMenu()" variant="outline-secondary"><i  v-bind:class="[sideCollapseBtn]"></i></b-button>

    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto">
        <li class="nav-item active"><span class="nav-link active">{{ page }}</span></li>

      </ul>
      <form class="form-inline my-2 my-lg-0">
        <b-button class="fw-button" variant="outline-success"><i class="fas fa-search"></i></b-button>
        <input class="form-control mr-lg-2" type="search" placeholder="Search" aria-label="Search">
      </form>
    </div>
  </nav>
</template>

<script>
export default {
  data: function () {
    return {
      sideCollapseBtn: 'fas fa-bars',
      collapsed: false
    }
  },
  props: ['page'],
  methods: {
    collapseSideMenu () {
      if (this.collapsed) {
        this.sideCollapseBtn = 'fas fa-bars'
        this.collapsed = false
        this.$emit('sideMenuBtnClicked', 250)
      } else {
        this.sideCollapseBtn = 'fas fa-ellipsis-v'
        this.collapsed = true
        this.$emit('sideMenuBtnClicked', 90)
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#navbar {
  background-color: white;
}

.fw-button {
  margin-left: auto;
  margin-right: auto;
  border-radius: 50%;
  width: 40px;
  height: 40px;
}
</style>
