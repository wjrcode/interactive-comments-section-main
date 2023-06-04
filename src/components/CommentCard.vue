<template>
  <div class="card">
    <div class="card__vote-button">
      <img src="../images/icon-plus.svg" class="card__icon" @click="upvote" />
      {{ score }}
      <img src="../images/icon-minus.svg" class="card__icon" @click="downvote" />
    </div>
    <div class="card__content">
      <div class="card__header">
        <div class="card__details">
          <div class="card__profile-photo">
            <img :src="photo" />
          </div>
          <div class="card__user-name">
            {{ name }}
          </div>
          <div class="card__time">
            {{ createdAt }}
          </div>
        </div>
        <div class="card__actions">
          <div class="card__button" v-if="!sameUser">
            <img src="../images/icon-reply.svg" />
            Reply
          </div>
          <div class="card__button card__button--red" v-if="sameUser" @click="deleteComment">
            <img src="../images/icon-delete.svg" />
            Delete
          </div>
          <div class="card__button" v-if="sameUser">
            <img src="../images/icon-edit.svg"  />
            Edit
          </div>
        </div>
      </div>
      <div class="card__comment">
        {{ comment }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommentCard',
  props: {
    id: Number,
    photo: String,
    name: String,
    createdAt: String,
    comment: String,
    score: Number,
    currentUser: String
  },
  computed: {
    sameUser() {
      return this.name == this.currentUser
    }
  },
  methods: {
    upvote() {
      this.$emit('vote', this.id, '+')
    },
    downvote() {
      this.$emit('vote', this.id, '-')
    },
    deleteComment(){
      this.$emit('deleteComment', this.id)
    }
  }
}
</script>

<style scoped>
.card {
  display: flex;
  background-color: white;
  padding: 2rem;
  border-radius: 0.5rem;
  gap: 1rem;
}

.card__vote-button {
  background-color: hsl(228, 33%, 97%);
  padding: 1rem;
  border-radius: 0.5rem;
  color: hsl(238, 40%, 52%);
  font-weight: bold;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  align-self: start;
}

.card__profile-photo img {
  width: 30px;
  aspect-ratio: 1/1;
}

.card__icon {
  width: 1rem;
}

.card__content {
  width: 100%;
}

.card__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.card__details {
  display: flex;
  align-items: center;
  gap: 1rem
}

.card__user-name {
  font-weight: bold;
}

.card__actions{
  display: flex;
  gap: 1rem;
}

.card__button {
  color: hsl(238, 40%, 52%);
  font-weight: bold;
}

.card__button--red {
  color: hsl(358, 79%, 66%);
}

.card__comment {
  margin-top: 1rem;
  text-align: left;
}
</style>
