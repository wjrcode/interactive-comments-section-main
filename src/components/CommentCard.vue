<template>
  <div class="card">
    <div class="card__vote-button"></div>
    <div class="card__content">
      <div class="card__header">
        <div class="card__details">
          <div class="card__profile-photo">
          

            <img :src="photo"/>
          </div>
          <div class="card__user-name">
            {{ name }}
          </div>
          <div class="card__time">
            {{ time }}
          </div>
        </div>
        <div class="card__reply-button"></div>
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
    photo: {type: String},
    name: String,
    time: String,
    comment: String
  },
  computed:{
    pic(){
      return require(this.photo)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
