<template>
  <div class="chatbox">
    <chatMessages/>
  </div>
</template>

<script>
import chatMessages from "~/components/chat-messages.vue";

export default {
  components: {
    chatMessages
  }
};
</script>

<style>
.chatbox {
  max-width: 768px;
  background-color: #ece5dd;
  padding: 1em;
  border-radius: 5px;
  border-left: 12px solid #dcf8c6;
  border-right: 12px solid #fff;
}
</style>
