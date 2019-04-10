<template>
  <div class="container">
    <headerTop/>
    <chatbox/>
  </div>
</template>

<script>
import headerTop from "~/components/header-top.vue";
import chatbox from "~/components/chatbox.vue";

export default {
  components: {
    headerTop,
    chatbox
  }
};
</script>

<style>
.container {
  max-width: 980px;
  margin: auto;
}
</style>
