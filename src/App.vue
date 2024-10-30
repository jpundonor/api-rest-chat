<script>
import Chat from "./components/Chat.vue";
export default {
  name: "App",
  components: {
    Chat,
  },
};
</script>

<template>
  <div class="container">
    <Chat />
  </div>
</template>

<style scoped>
.container {
  max-width: 1280px;
  margin: auto;
}
</style>
