<template>
  <div class="chat-container">
    <UserChat :user="user1" color="#90EEA3" position="flex-start" @send="sendMessage" />
    <ChatBox :messages="messages" />
    <UserChat :user="user2" color="#C9AFCB" position="end" @send="sendMessage" />
  </div>
</template>

<script>
import axios from "axios";
import UserChat from "./UserCard.vue";
import ChatBox from "./ChatBox.vue";

export default {
  name: "Chat",
  components: {
    UserChat,
    ChatBox,
  },
  data() {
    return {
      user1: {},
      user2: {},
      messages: [],
    };
  },
  async created() {
    this.user1 = await this.fetchUser();
    this.user2 = await this.fetchUser();
  },
  methods: {
    async fetchUser() {
      const response = await axios.get("https://randomuser.me/api/");
      return response.data.results[0];
    },
    sendMessage(message) {
      this.messages.push(message);
    },
  },
};
</script>

<style scoped>
.chat-container {
  display: flex;
  justify-content: space-between;
  gap: 1rem;
  width: 100%;
}
</style>
