<template>
  <div class="user-chat">
    <img :src="user.picture?.large" alt="user.name" />
    <span>{{ user.name?.first }} {{ user.name?.last }}</span>
    <input type="color" v-model="messageColor" />
    <textarea rows="6" v-model="textUser"></textarea>
    <button @click="send">Enviar</button>
  </div>
</template>

<script>
export default {
  name: "UserChat",
  props: {
    user: Object,
    color: String,
    position: String,
  },
  data() {
    return {
      textUser: "",
      messageColor: this.color,
    };
  },
  methods: {
    send() {
      if (!this.textUser) return;
      const message = {
        text: this.textUser,
        author: `${this.user.name.first} ${this.user.name.last}`,
        color: this.messageColor,
        textPosition: this.position,
      };
      this.$emit("send", message);
      this.textUser = "";
    },
  },
};
</script>

<style scoped>
.user-chat {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  width: max-content;
  height: max-content;
}
input {
  width: 100%;
}
textarea {
  resize: none;
}
</style>
