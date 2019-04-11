<template>
  <div class="container">
    <headerTop/>
    <div class="container__flex">
      <chatbox/>
      <chatOptions/>
    </div>
  </div>
</template>

<script>
import headerTop from "~/components/header-top.vue";
import chatbox from "~/components/chatbox.vue";
import chatOptions from "~/components/chat-options.vue";

export default {
  components: {
    headerTop,
    chatbox,
    chatOptions
  }
};
</script>

<style>
.container {
  max-width: 980px;
  margin: auto;
}

.container__flex {
  display: flex;
}
</style>
