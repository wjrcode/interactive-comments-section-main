<template>
  <main>
    <template v-for="(comment, i) in comments" :key="`item-${i}`">
      <div>
        <CommentCard v-bind="i" :name="comment.user.username" :photo="comment.user.image.png" :comment="comment.content"
          :createdAt="comment.createdAt" :score="comment.score" :id="comment.id" @vote="vote" :currentUser="currentUser.username" @deleteComment="deleteComment"/>
        <div class="reply__section">
          <div class="barra"></div>
          <div class="replies">
            <template v-for="(reply, j) in comment.replies" :key="`item-${j}`">
              <CommentCard v-bind="j" :name="reply.user.username" :photo="reply.user.image.png" :comment="reply.content"
                :createdAt="reply.createdAt" :score="reply.score" />
            </template>
          </div>
        </div>
      </div>

    </template>
    <CommentInput :photo="currentUser.image.png" :name="currentUser.username" @sendComment="sendComment" />
    <div class="attribution">
      Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>.
      Coded by <a href="#">Your Name Here</a>.
    </div>
  </main>
</template>

<script>
import CommentCard from './components/CommentCard.vue';
import data from './data/data.json'
import CommentInput from './components/CommentInput.vue';

export default {
  name: 'App',
  components: {
    CommentCard,
    CommentInput
  },
  computed: {
    pic() {
      return '/images/avatars/image-amyrobson.png'
    }
  },
  data: function () {
    return {
      comments: data.comments,
      currentUser: data.currentUser
    }
  },
  methods: {
    sendComment(comment) {
      this.comments.push(comment)
    },
    vote(id, operation) {
      const comment = this.comments.find(c => c.id === id)
      if (comment) {
        comment.score = operation == '+' ? comment.score + 1 : (comment.score == 0 ? 0 : comment.score - 1)
      }
    },
    deleteComment(id){
      this.comments = this.comments.filter(comment => comment.id != id)
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Rubik:wght@400;500;700&display=swap');

.v-application {
  font-family: "Rubik";
}

textarea,
button {
  font-family: "Rubik";
  font-size: 16px;
}

html {
  font-family: "Rubik";
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100%;
}

body {
  margin: 0;
  background-color: hsl(228, 33%, 97%);
}

main {
  max-width: 50rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  font-family: "Rubik";
}

.attribution {
  font-size: 11px;
  text-align: center;
  margin-top: 1rem;
}

.attribution a {
  color: hsl(228, 45%, 44%);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.reply__section {
  margin-left: 3rem;
  margin-top: 1rem;
  display: flex;
}

.barra {
  width: 0.5rem;
  background-color: hsl(223, 19%, 93%);
  margin-top: 4px;
  margin-right: 3rem;
}

.replies {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
</style>
