<template>
  <chatMessages/>
</template>

<script>
import chatMessages from "~/components/chat-messages.vue";

export default {
  components: {
    chatMessages
  }
};
</script>

<style lang="scss">
.chatbox {
  max-width: 768px;
  height: 520px;
  overflow: scroll;
  overflow-x: hidden;
  width: 100%;
  background-color: #ece5dd;
  border-radius: 5px;
  position: relative;

  &::-webkit-scrollbar {
    display: none;
  }
}

@media (max-width: 500px) {
  .chatbox {
    border-radius: 0;
  }
}
</style>
