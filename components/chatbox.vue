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
}
</style>
