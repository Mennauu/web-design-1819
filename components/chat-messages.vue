<template>
  <ul class="messages">
    <li class="messages__item">
      <img src="/joe-rogan.jpg" alt="Joe Rogan" class="messages__image">
      <p
        class="messages__text"
      >My guest today is a great man that is a gem and you might have seen him on television for decades giving advice and being on point and he's just a cool guy to hang out with I really enjoy him I'm very good friends with his son so thank you Jay for setting it up please welcome the Great and Powerful Dr. Phil</p>
    </li>
    <li class="messages__item">
      <p
        class="messages__text"
        style="text-align: right; margin-right: 1em;"
      >He'll let him worry out of all the years you've been doing your show and all the years you could give advice how do they catch me outside girl lives with her mother and her mother actually brings her on a course and she's Trainwreck and we work with her and we send her to this Ranch for like 4 months right she goes for a long time and makes a complete turnaround become a leader she's working with all these girls doing a great job</p>
      <img src="/dr-phil.jpg" alt="Joe Rogan" class="messages__image">
    </li>
  </ul>
</template>

<style lang="scss">
.messages__item {
  display: flex;
  background: #fff;
  padding: 1em;
  margin-bottom: 0.5em;
  border-radius: 5px;
}

.messages__item:nth-child(odd) {
  background: lightgray;
}

.messages__image {
  width: 80px;
  height: 80px;
  max-width: 100%;
  border-radius: 50%;
  margin-right: 1em;
}

.message {
}
</style>
