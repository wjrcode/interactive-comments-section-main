<template>
    <div class="card">
        <div class="card__vote-button" v-if="edit">
            <img src="../images/icon-plus.svg" class="card__icon" />
            {{ score }}
            <img src="../images/icon-minus.svg" class="card__icon" />
        </div>
        <div class="card__content">
            <div class="card__header" v-if="edit">
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
            </div>
            <div class="card__comment">
                <div class="card__profile-photo">
                    <img :src="photo" />
                </div>
                <input class="card__input" v-model="newComment" placeholder="Add a comment..." />
                <button class="card__button" @click="sendComment()">send</button>
            </div>

        </div>
    </div>
</template>
  
<script>
export default {
    props: {
        photo: String,
        name: String,
        createdAt: String,
        comment: String,
        score: Number,
        edit: Boolean
    },
    data: function () {
        return {
            newComment: this.comment
        }
    },
    methods: {
        sendComment() {
            const comment = {
                user: {
                    image: {
                        png: this.photo
                    },
                    username: this.name
                },
                content: this.newComment,
                score: 0,
                createdAt: this.createdAt,
            }
            this.$emit('sendComment', comment )
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
    justify-content: space-between;
    max-height: 5.6rem;
}

.card__icon {
    width: 1rem;
}

.card__profile-photo img {
    width: 30px;
    aspect-ratio: 1/1;
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

.card__reply-button {
    color: hsl(238, 40%, 52%);
    font-weight: bold;
}

.card__comment {
    display: flex;
    gap: 1rem;
}

.card__input {
    width: 100%;
    border-radius: 0.3rem;
    border: solid 1px hsl(223, 19%, 93%);
    padding: 1rem;
    outline: none;
}

.card__input:focus {
    border: solid 1px hsl(238, 40%, 52%);
}

.card__button {
    background-color: hsl(238, 40%, 52%);
    border: none;
    border-radius: 0.5rem;
    color: white;
    font-weight: bold;
    text-transform: uppercase;
    width: 7rem;
}
</style>
  