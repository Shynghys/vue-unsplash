<template>
  <div class="comments">
    <div class="comment">
      <img
        class="comment__profile media__obj"
        :src="author.profile_image.small"
        :alt="author.name"
      />
      <div class="comment__block">
        <div class="comment__header">
          <div class="comment__author">{{ author.name }}</div>
          <div class="comment__date">{{ date }}</div>
        </div>
        <div class="comment__body">
          <div class="comment__text">{{ comment }}</div>
        </div>
      </div>
    </div>

    <div class="comment">
      <img
        class="comment__profile media__obj"
        :src="author.profile_image.small"
        :alt="author.name"
      />
      <div class="comment__block">
        <div class="comment__leave">
          <input type="text" name="" id="" placeholder="Оставьте комменатрий" />
        </div>
        <div class="comment__confirm">
          <b-button variant="outline-info" class="comment__button"
            >Отмена</b-button
          >
          <b-button variant="outline-success">Отправить</b-button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    author: {},
    comment: {},
    date: {}
  }
}
</script>
<style>
input {
  outline: none;
  border: none;
  width: 100%;
}
.comments {
  display: grid;
  grid-template: auto/1fr;
  gap: 50px;
}
.comment__block {
  display: flex;
  flex-direction: column;
}
.comment__header {
  display: flex;
  align-items: center;
}
.comment__author {
  font-weight: 600;
  margin-right: 15px;
}
.comment__date {
  font-size: 12px;
  font-style: italic;
}
.comment__leave {
  border-bottom: 2px solid black;
}
.comment__confirm {
  margin-top: 20px;
  display: flex;
  align-items: flex-end;
  justify-content: flex-end;
}
.comment__button {
  margin-right: 20px;
}
</style>
