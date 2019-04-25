<template>
  <div class="container">
    <headerTop/>
    <chatbox/>
  </div>
</template>

<script>
import headerTop from "~/components/header-top.vue";
import chatbox from "~/components/chat-box.vue";

export default {
  components: {
    headerTop,
    chatbox
  }
};
</script>

<style>
.container {
  max-width: 1100px;
  margin: auto;
}

.container__flex {
  display: flex;
  position: relative;
}
</style>
