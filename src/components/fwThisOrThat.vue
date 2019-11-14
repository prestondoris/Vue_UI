<template>
  <div id="buttonGroup">
    <button id="thisBtn" :class="thisClass"><slot name="thisSlot"></slot></button>
    <span id="or">or</span>
    <button id="thatBtn" :class="thatClass"><slot name="thatSlot"></slot></button>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
    }
  },
  props: {
    thisClass: String,
    thatClass: String,
    thisVal: String,
    thatVal: String
  }
}
</script>

<style scoped>
#buttonGroup {
  display: inline;
}
#or {
  width: 25px;
  height: 25px;
  display: inline-block;
  border-radius: 50%;
  z-index: 10;
  background-color: white;
  font-size: 1.5em;
  margin-top: auto;
  margin-bottom: auto;
}

button {
  display: inline-block;
}

#thisBtn {
  position: relative;
  right: -9px;
  z-index: -1;
}

#thatBtn {
  position: relative;
  left: -9px;
  z-index: -1;
}
</style>
