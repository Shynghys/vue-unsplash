<template>
  <div class="grid__item card">
    <div class="card__body">
      <img :src="photo.urls.regular" :alt="photo.description" />
    </div>
  </div>
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
  methods: {},
  filters: {
    formatDate(value) {
      return moment(value).format('LL')
    }
  }
}
</script>
