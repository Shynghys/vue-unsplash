<template>
  <b-modal class="grid__item modal" id="modal-1" size="xl" title=""
    ><b-button
      type="button"
      class="btn-close close"
      aria-label="Close"
      @click="$bvModal.hide('modal-1')"
    ></b-button>
    <div class="card__header">
      <h1>
        {{ photo.description ? photo.description : photo.alt_description }}
      </h1>
    </div>

    <div class="card__body mt-5">
      <img
        :src="photo.urls ? photo.urls.regular : ''"
        :alt="photo.description"
      />
    </div>
    <div class="card__footer media mt-5">
      <div class="media__body">
        <img
          :src="photo.user ? photo.user.profile_image.medium : ''"
          :alt="photo.user.name"
          class="media__obj"
        />
        <div>
          <span class="card__likes">
            <i
              :class="isLiked ? 'far fa-heart' : 'fas fa-heart'"
              @click="isLiked = !isLiked"
            />
            {{ photo.likes + (isLiked ? 0 : 1) }}
          </span>

          <span class="card__date">
            <i class="fa fa-calendar-o"></i>
            {{ photo.created_at | formatDate }}
          </span>
        </div>
      </div>
      <div class="media__comments mt-5">
        <commentary
          :author="photo.user"
          :comment="
            photo.description ? photo.description : photo.alt_description
          "
          :date="photo.created_at | formatDate"
        />
      </div>
    </div>
  </b-modal>
</template>

<script>
import Commentary from './Commentary.vue'
import moment from 'moment'

export default {
  data() {
    return { isLiked: false }
  },
  components: { Commentary },
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
<style>
.modal-footer,
.modal-header {
  display: none !important;
}
</style>
