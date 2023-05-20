<template>
  <div class="card">
    <div class="card__vote-button">
      <img src="../images/icon-plus.svg" class="card__icon" />
      {{ score }}
      <img src="../images/icon-minus.svg" class="card__icon" />
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
        <div class="card__reply-button">
          <img src="../images/icon-reply.svg" />
          Reply
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
    photo: String,
    name: String,
    createdAt: String,
    comment: String,
    score: Number
  },
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
  justify-content: space-between;
  max-height: 5.6rem;
}

.card__icon {
  width: 1rem;
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

.card__reply-button {
  color: hsl(238, 40%, 52%);
  font-weight: bold;
}

.card__comment {
  margin-top: 1rem;
  text-align: left;
}
</style>
