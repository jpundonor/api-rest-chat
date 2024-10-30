<template>
  <div class="chat-box">
    <div
      class="chat-container"
      v-for="(message, index) in messages"
      :key="index"
      :style="{alignItems: message.textPosition}"
    >
      <span class="chat-author">{{ message.author }}</span>
      <div class="chat-messages" :style="{ backgroundColor: message.color }">
        {{ message.text }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ChatBox",
  props: {
    messages: Array,
  },
  updated() {
    this.$el.scrollTop = this.$el.scrollHeight;
  },
};
</script>

<style scoped>
.chat-box {
  width: 100%;
  height: 370px;
  overflow-y: auto;
  border: 1px solid black;
  background-color: gainsboro;
  padding: 10px;
}
.chat-container {
  display: flex;
  flex-direction: column;
  gap: 5px;
}
.chat-messages {
  padding: 0.5rem;
  width: max-content;
  border-radius: 10px;
  margin-bottom: 10px;
}
span {
  font-size: 14px;
  color: #5a5a5a;
}
</style>
