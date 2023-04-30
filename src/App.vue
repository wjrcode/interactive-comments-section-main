<template>
  <main>
    <template v-for="(comment, i) in comments" :key="`item-${i}`">
      <CommentCard v-bind="i" :name="comment.user.username" :photo="comment.user.image.png" :comment="comment.content" />
    </template>
    <div class="attribution">
      Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>.
      Coded by <a href="#">Your Name Here</a>.
    </div>
  </main>
</template>

<script>
import CommentCard from './components/CommentCard.vue';
import data from './data/data.json'

export default {
  name: 'App',
  components: {
    CommentCard
  },
  computed: {
    pic() {
      return '/images/avatars/image-amyrobson.png'
    }
  },
  data: function () {
    return {
      comments: data.comments,
      imgPath: './images/avatars/image-amyrobson.png'
    }
  },
  beforeMount() {
    window.console.log(data.comments)
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Rubik:wght@400;500;700&display=swap');

.v-application {
  font-family: "Space Mono";
}

html {
  font-family: "Space Mono";
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100%;
}

body {
  margin: 0;
  background-color: hsl(185, 41%, 84%);
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
</style>
