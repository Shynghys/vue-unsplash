<template>
  <div class="grid__item"></div>
</template>

<script>
import moment from 'moment'

export default {
  props: {
    photo: {
      type: Object,
      required: true
    }
  },
  methods: {
    hide() {
      this.$modal.hide('modal')
    }
  },
  filters: {
    formatDate(value) {
      return moment(value).format('LL')
    }
  }
}
</script>
