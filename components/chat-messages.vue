<template>
  <ul class="messages">
    <li
      class="messages__item"
      :class="'messages__item--' + item.position"
      v-for="(item, index) in items"
      :key="index"
    >
      <div class="messages__container">
        <img :src="item.image" :alt="item.name" class="messages__image">
        <p class="messages__text">{{item.message}}</p>
        <small class="messages__timestamp">{{item.timestamp}}</small>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          image: "joe-rogan.jpg",
          message:
            "Ha, ha, ha. Four, three, two, one. Boom. Thank you. Thanks for doing this, man. Really appreciate it.",
          name: "Joe Rogan",
          position: "left",
          timestamp: "00:01"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message: "Your welcome.",
          position: "right",
          timestamp: "00:09"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "It’s very good to meet you.",
          position: "left",
          timestamp: "00:10"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message: "Nice to meet you too.",
          position: "right",
          timestamp: "00:11"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "And thanks for not lighting this place on fire.",
          position: "left",
          timestamp: "00:12"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message: "Your welcome. That’s coming later.",
          position: "right",
          timestamp: "00:13"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "*Laughing*",
          position: "center",
          timestamp: "00:14"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message:
            "How does one, just in the middle of doing all the things you do, create cars, rockets, all this stuff you’re doing, constantly innovating, decide to just make a flame thrower? Why do you have the time for that?",
          position: "left",
          timestamp: "00:16"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message:
            "Well, the thing… I wouldn’t put a lot of time into the flame thrower. This was an off the cuff thing. So I have sort of like a, sort of a hobby company called The Boring Company, which started out as a joke, and we decided to make it real, and dig a tunnel under L.A. And then other people asked us to dig tunnels. And so we said yes in a few cases.",
          position: "right",
          timestamp: "00:30"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message:
            "And we have a merchandise section that only has one piece of merchandise at a time. And we started off with a cap. And there was only one thing on… It was just Boring Company.com/cap or hat. That’s it. And then we sold the hats. Limited edition. It just said the Boring Company. And then I’m a big fan of Spaceballs the movie. And in Spaceballs Yogurt goes through the merchandising section and they have a flame thrower, in the merchandising section of Spaceballs. And the kids loved that one. That’s the line of when he pulls out the flame thrower. So I was like, we should do a flame thrower. So we…",
          position: "right",
          timestamp: "01:02"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message:
            "Does anybody tell you no? Does anybody go, “Elon, um, maybe for yourself. But selling a flame thrower, the liabilities, all the people you’re selling this devise to. What kind of an unhinged people are going to be buying a flame thrower in the first place? Do we really want to connect ourselves to all these potential arsonists?”",
          position: "left",
          timestamp: "01:52"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message:
            "Yeah, it’s a terrible idea. Terrible. You shouldn’t buy one. I said don’t buy this flame thrower. Don’t buy it. Don’t buy it. That’s what I said. But still people bought it.",
          position: "right",
          timestamp: "02:11"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "*Intense laughing*",
          position: "center",
          timestamp: "02:12"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "Yeah. They’re not gonna listen.",
          position: "left",
          timestamp: "02:23"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message: "There’s nothing I can do to stop them. I cannot stop them.",
          position: "right",
          timestamp: "02:23"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "You build it, they will come.",
          position: "left",
          timestamp: "02:25"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message: "I said don’t buy it. It’s a bad idea.",
          position: "right",
          timestamp: "02:26"
        }
      ]
    };
  },

  mounted() {
    const timer = () => {
      let totalSeconds = 0;

      setInterval(() => {
        ++totalSeconds;
        const hour = Math.floor(totalSeconds / 3600);
        const minute = Math.floor((totalSeconds - hour * 3600) / 60);
        const seconds = totalSeconds - (hour * 3600 + minute * 60);
        const time = ("0" + minute).slice(-2) + ":" + ("0" + seconds).slice(-2);

        showMessage(time);
      }, 1000);
    };

    const getTimestampElements = async () => {
      return await document.querySelectorAll(".messages__timestamp");
    };

    const showMessage = async time => {
      const timestampElements = await getTimestampElements();

      for await (let timestamp of timestampElements) {
        const timeFromElement = timestamp.innerText;
        const messageElement = timestamp.parentNode.parentNode;

        if (time === timeFromElement) {
          messageElement.classList.add("visible");
        }
      }
    };

    timer();
  }
};
</script>

<style lang="scss">
.visible {
  transition: 0.5s;
  opacity: 1 !important;
}

.messages__item {
  margin-bottom: 0.5em;
  width: 100%;
  display: flex;
  opacity: 0;
}

.messages__container {
  display: inline-flex;
  padding: 0.6em;
  border-radius: 5px;
  position: relative;
}

.messages__image {
  width: 3.75em;
  height: 3.75em;
  max-width: 100%;
  border-radius: 50%;
}

.messages__text {
  align-self: center;
}

.messages__timestamp {
  color: gray;
  position: absolute;
  bottom: 0;
  padding: 0.5em;
  border-radius: 5px;
}

/* Left message */
.messages__item--left {
  justify-content: flex-start;

  .messages__container {
    background-color: #dcf8c6;
  }

  .messages__image {
    margin-right: 0.6em;
  }

  .messages__timestamp {
    background-color: #dcf8c6;
    left: -2.5em;
  }
}

/* Right message */
.messages__item--right {
  justify-content: flex-end;

  .messages__container {
    background-color: #fff;
    flex-direction: row-reverse;
  }

  .messages__image {
    margin-left: 0.6em;
  }

  .messages__timestamp {
    background-color: #fff;
    right: -2.5em;
  }
}

/* Center message */
.messages__item--center {
  justify-content: center;
  padding: 1em;
  margin-bottom: 0.9em;

  .messages__container {
    background-color: #bdb7b1;
    padding: 0.3em;
  }

  .messages__image {
    margin-right: 0.6em;
    width: 40px;
    height: 40px;
  }

  .messages__text {
    font-size: calc(12px + (16 - 12) * ((100vw - 300px) / (1100 - 300)));
  }

  .messages__timestamp {
    background-color: #bdb7b1;
    left: 50%;
    transform: translateX(-50%);
    bottom: -0.9em;
    color: #000;
  }
}
</style>
