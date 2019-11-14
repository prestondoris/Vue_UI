<template>
  <div class="about">
    <h1>This is the Components Testing page</h1>
    <fw-this-or-that v-bind="buttonData">
      <template v-slot:thisSlot>Test</template>
      <template v-slot:thatSlot><i class="fas fa-clipboard-list icon"></i></template>
    </fw-this-or-that>
  </div>
</template>

<script>
import fwThisOrThat from '@/components/fwThisOrThat.vue'
export default {
  data: function () {
    return {
      buttonData: {
        thisClass: 'btn btn-primary',
        thatClass: 'btn btn-primary'
      }
    }
  },
  components: {
    fwThisOrThat
  }
}
</script>
