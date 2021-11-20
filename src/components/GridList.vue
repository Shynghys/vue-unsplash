<template>
  <div>
    <modal
      name="modal"
      class="modal"
      :height="500"
      :width="800"
      resaziable
      :adaptive="true"
    >
      <button type="button" class="close" aria-label="Close" @click="hide">
        <span aria-hidden="true">&times;</span>
      </button>
      <modal-item :photo="currentPhoto"
    /></modal>

    <div class="filters">
      <label for="sort">Sort by</label>
      <select
        name="sort"
        v-model="photo.orderBy"
        @change="fetchPhotos(photo.page, $event.target.value)"
      >
        <option value="latest">Latest</option>
        <option value="oldest">Oldest</option>
        <option value="popular">Popular</option>
      </select>
    </div>

    <div class="loader" v-if="photo.loadState == LOAD_STATE.LOADING"></div>

    <div class="grid" v-if="photo.loadState == LOAD_STATE.SUCCESS">
      <GridItem
        v-for="photo in photo.photos"
        :key="photo.id"
        :photo="photo"
        @click.native="showModal(photo)"
      />
    </div>
    <Pagination @onPageChanged="fetchPhotos" />
  </div>
</template>

<script>
import GridItem from './GridItem'
import ModalItem from './Modal'
import Pagination from './Pagination'
import partials from '@/store/partials'

import { mapState, mapActions } from 'vuex'

export default {
  data() {
    return {
      ...partials,
      currentPhoto: {}
    }
  },

  components: {
    GridItem,
    ModalItem,
    Pagination
  },
  methods: {
    showModal(photo) {
      console.log('aa')
      this.currentPhoto = photo
      this.$modal.show('modal')
    },
    hide() {
      this.$modal.hide('modal')
    },
    fetchPhotos(page, order) {
      this.$store.dispatch('photo/fetch', {
        page,
        order: this.photo.orderBy
      })
    }
  },
  computed: mapState(['photo']),
  mounted() {
    // this.show()
    this.fetchPhotos(this.photo.page)
  }
}
</script>
