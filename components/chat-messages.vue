<template>
  <div class="container__flex">
    <div class="chatbox">
      <ul class="messages">
        <li
          class="messages__item"
          :class="['messages__item--' + item.position]"
          v-for="(item, index) in items"
          :key="index"
        >
          <div class="messages__container">
            <img :src="item.image" :alt="item.name" class="messages__image">
            <p class="messages__text--placeholder">{{item.message}}</p>
            <p class="messages__text"></p>
            <small class="messages__timestamp">{{item.timestamp}}</small>
            <span class="tooltip">
              <strong>{{item.name}}</strong>
              <br>
              {{item.timestamp}}
            </span>
          </div>
        </li>
      </ul>
      <div class="people">
        <div class="guy">
          <img src="joe-rogan.jpg" alt="Joe">
          <strong>Joe Rogan</strong>
          <br>
          <span>Host</span>
        </div>
        <div class="guy">
          <img src="elon-musk.jpg" alt="Elon Musk">
          <strong>Elon Musk</strong>
          <br>
          <span class="guest">Guest</span>
        </div>
      </div>
      <button class="play">
        &#9658;
        <br>
        <span>Ready? Start podcast</span>
      </button>
    </div>
    <div class="elements">
      <ul>
        <li class="flamethrower">
          <div class="side-element"></div>
          <h3>The flamethrower</h3>
          <img src="/boring-company-flamethrower.png" alt="flamethrower">
        </li>
        <li class="hat">
          <div class="side-element"></div>
          <h3>The Boring Company Hat</h3>
          <img src="/boring-company-hat.png" alt="The Boring Company Hat">
        </li>
      </ul>
    </div>
    <!-- <div class="options">
      <ul>
        <li>
          <strong>Speed</strong>
          <input type="radio" id="50" value="0.50" v-model="selected">
          <label for="50">0.5</label>
          <input type="radio" id="75" value="0.75" v-model="selected">
          <label for="75">0.75</label>
          <input type="radio" id="1" value="1" v-model="selected">
          <label for="1">1</label>
          <input type="radio" id="125" value="1.25" v-model="selected">
          <label for="125">1.25</label>
          <input type="radio" id="150" value="1.50" v-model="selected">
          <label for="150">1.50</label>
          <input type="radio" id="175" value="1.75" v-model="selected">
          <label for="175">1.75</label>
          <input type="radio" id="2" value="2" v-model="selected">
          <label for="2">2</label>
        </li>
        <li>* Begin vanaf een bepaald tijdstip</li>
        <li>* Bepaal snelheid (originele snelheid van podcast, 1.25x, 1.5x, 2x, 100x??)</li>
        <li>* Bepaal hoeveelheid "center berichten"</li>
        <li>* Typ de tekst</li>
      </ul>
    </div>-->
  </div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  data() {
    return {
      opacity: "opacity-layer",
      visible: "visible",
      showAll: [],
      selected: "1",
      items: [
        {
          image: "joe-rogan.jpg",
          message:
            "",
          name: "Joe Rogan",
          position: "left",
          timestamp: "00:00:00"
        },
        {
          image: "joe-rogan.jpg",
          message:
            "Four, three, two, one. Boom. Thank you. Thanks for doing this, man. Really appreciate it.",
          name: "Joe Rogan",
          position: "left",
          timestamp: "00:00:01"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message: "Your welcome.",
          position: "right",
          timestamp: "00:00:09"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "It’s very good to meet you.",
          position: "left",
          timestamp: "00:00:10"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message: "Nice to meet you too.",
          position: "right",
          timestamp: "00:00:13"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "And thanks for not lighting this place on fire.",
          position: "left",
          timestamp: "00:00:15"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message: "Your welcome. That’s coming later.",
          position: "right",
          timestamp: "00:00:18"
        },
        {
          image: "joe-rogan-laughing.gif",
          name: "Joe Rogan",
          message: "*Laughing*",
          position: "center",
          timestamp: "00:00:20"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message:
            "How does one, just in the middle of doing all the things you do, create cars, rockets, all the stuff you're doing, constantly innovating, decide to just make a flamethrower? Where do you have the time for that?",
          position: "left",
          timestamp: "00:00:22"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message:
            "Well, the flame, we didn't put a lot of time into the flamethrower. This was an off-the-cuff thing. It's sort of a hobby company called the Boring Company, which started out as a joke, and we decided to make a real, and dig a tunnel under LA. And then, other people asked us to dig tunnels. And so, we said yes in a few cases.",
          position: "right",
          timestamp: "00:00:36"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "Now, who-",
          position: "left",
          timestamp: "00:01:07"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message:
            "And then, we have a merchandise at a time. And we started off with a cap. And there was only one thing on, which is BoringCompany.com/hat. That's it. And then, we sold the hats, limited edition. It just said, “The Boring Company”. And then, I'm a big fan of Spaceballs, the movie. And in Spaceballs, Yogurt goes through the merchandising section, and they have a flamethrower in the merchandising section of Spaceballs. And, like, the kids love that one. That's the line when he pulls up the flamethrower. It's like, “We should do a flamethrower”. So, we-",
          position: "right",
          timestamp: "00:01:09"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message:
            "Does anybody tell you no? Does anybody go, “Elon, maybe for yourself, but selling a flamethrower, the liabilities, all the people you're selling this device to, what kind of unhinged people are going to be buying a flamethrower in the first place? Do we really want to connect ourselves to all these potential arsonists?”",
          position: "left",
          timestamp: "00:01:58"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message:
            "Yeah, it’s a terrible idea. Terrible. You shouldn’t buy one.",
          position: "right",
          timestamp: "00:02:18"
        },
        {
          image: "joe-rogan-laughing.gif",
          name: "Joe Rogan",
          message: "*Laughing*",
          position: "center",
          timestamp: "00:02:21"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message:
            "I said, “don’t buy this flame thrower. Don’t buy it. Don’t buy it.” That’s what I said. But still people bought it.",
          position: "right",
          timestamp: "00:02:22"
        },
        {
          image: "elon-musk-flamethrower.gif",
          name: "Elon Musk",
          message: "Flamethrower",
          position: "center",
          timestamp: "00:02:28"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "Yeah. They’re not gonna listen.",
          position: "left",
          timestamp: "00:02:32"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message:
            "There’s nothing I can do to stop them. I did not stop them.",
          position: "right",
          timestamp: "00:02:36"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "You build it, they will come.",
          position: "left",
          timestamp: "00:02:39"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message: "I said, “don’t buy it. It’s a bad idea.”",
          position: "right",
          timestamp: "00:02:41"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "How many did you make?",
          position: "left",
          timestamp: "00:02:44"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message:
            "It's dangerous. It's wrong. Don't buy it. And, still, people bought it. I just couldn't stop them.",
          position: "right",
          timestamp: "00:02:46"
        },
        {
          image: "elon-musk-laughing.gif",
          name: "Elon Musk",
          message: "Laughing",
          position: "center",
          timestamp: "00:02:50"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "How many did you make?",
          position: "left",
          timestamp: "00:02:53"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message: "We made 20000.",
          position: "right",
          timestamp: "00:02:55"
        },
        {
          image: "joe-rogan-suprised.gif",
          name: "Joe Rogan",
          message: "*Suprised*",
          position: "center",
          timestamp: "00:02:57"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "And they're all gone?",
          position: "left",
          timestamp: "00:02:59"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message:
            "In three -- I think, four days. They sold out in four days.",
          position: "right",
          timestamp: "00:03:01"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "Are you going to do another run?",
          position: "left",
          timestamp: "00:03:05"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message: "No.",
          position: "right",
          timestamp: "00:03:07"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "No, that's it?",
          position: "left",
          timestamp: "00:03:08"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message: "Yes.",
          position: "right",
          timestamp: "00:03:09"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message: "Oh, I see..",
          position: "left",
          timestamp: "00:03:10"
        },
        {
          image: "elon-musk.jpg",
          name: "Elon Musk",
          message:
            "I said we're doing 20. We did 50000. 50000 hats, and that was a million dollars. I thought, “Okay. Well, we'll sell something for 10 million,“ and that was 20000 flamethrowers at $500 each. They went fast.",
          position: "right",
          timestamp: "00:03:12"
        },
        {
          image: "joe-rogan.jpg",
          name: "Joe Rogan",
          message:
            "Yeah. How do you have the time? How do you have the time to do that though? I mean, I understand that it's not a big deal in terms of all the other things you do, but how do you have time to do anything? I just -- I don't understand your time management skills.",
          position: "left",
          timestamp: "00:03:28"
        }
      ]
    };
  },

  mounted() {
    const play = document.querySelector(".play");
    const people = document.querySelector(".people")

    const getMessages = () => this.items;

    // const getMessagesText = async () => {
    //   const messages = await getMessages()
    //   const messagesText = []

    //   for await (let message of messages) {
    //     messagesText.push(message.message)
    //   }

    //   return messagesText
    // }

    const getMessageNoEmotion = async () => {
      const messages = await getMessages();
      const messagesNoEmotion = [];

      for await (let message of messages) {
        if (message.position === "left" || message.position === "right") {
          messagesNoEmotion.push(message);
        }
      }

      return messagesNoEmotion;
    };

    const getMessageElementNoEmotion = async () => {
      const elements = document.querySelectorAll(".messages__text");
      const elementsList = [];

      for await (let element of elements) {
        const parent = element.parentNode.parentNode;
        if (!parent.classList.contains("messages__item--center")) {
          elementsList.push(element);
        }
      }

      return elementsList;
    };

    const getMessageElement = async () => {
      const elements = document.querySelectorAll(".messages__text");
      const elementsList = [];

      for await (let element of elements) {
        elementsList.push(element);
      }

      return elementsList;
    };

    const timer = () => {
      let count = 0;
      play.classList.add("hidden");
      people.classList.add("hidden")

      setInterval(() => {
        count++;

        const hour = Math.floor(count / 3600);
        const minute = Math.floor((count - hour * 3600) / 60);
        const seconds = count - (hour * 3600 + minute * 60);
        const time =
          ("0" + hour).slice(-2) +
          ":" +
          ("0" + minute).slice(-2) +
          ":" +
          ("0" + seconds).slice(-2);

        showMessage(time);
      }, 1000 / 1.5);
    };

    const showMessage = async time => {
      const messages = await getMessages();
      const messagesWithoutEmotion = await getMessageNoEmotion();
      const elements = await getMessageElement();
      const messagesElementsWithoutEmotion = await getMessageElementNoEmotion();

      const flamethrower = document.querySelector(".flamethrower");
      const hat = document.querySelector(".hat");

      if (time === "00:00:38") {
        flamethrower.classList.add("visible-element");
      }

      if (time === "00:00:52") {
        flamethrower.classList.remove("visible-element");
      }

      if (time === "00:01:20") {
        hat.classList.add("visible-element");
      }

      if (time === "00:01:34") {
        hat.classList.remove("visible-element");
      }

      elements.forEach((message, index) => {
        const timestamp = message.parentNode.children[3].innerText;

        if (time === timestamp) {
          const parent = message.parentNode.parentNode;
          const messagesElement = document.querySelector(".messages");

          if (!parent.classList.contains("messages__item--center")) {
            const elementTime = timestamp;
            const elementTimeToDate = toDate(elementTime, "h:m:s");

            const nextElementTime =
              elements[index + 1].parentNode.children[3].innerText;
            const nextElementTimeToDate = toDate(nextElementTime, "h:m:s");
            const msgInMs = nextElementTimeToDate - elementTimeToDate;

            const messageInWords = messages[index].message.match(/\b(\w+\W+)/g)


            // message.textContent = messages[index].message;
            typeWriter(messageInWords, message, msgInMs);

          } else {
            message.textContent = messages[index].message;
          }

          const previousParent = elements[index - 1]

          previousParent.classList.add(this.opacity)

          parent.classList.add(this.visible);

          parent.scrollIntoView({
            behavior: "smooth",
            block: "end"
          });

          // const scrollAmount = messages[index].message.length / 1.8;

          // if (scrollAmount < 60) {
          //   messagesElement.scrollTop += 60;
          // } else {
          //   messagesElement.scrollTop += scrollAmount;
          // }
        }
      });
    };

    const toDate = (dStr, format) => {
      let now = new Date();

      if (format == "h:m:s") {
        now.setHours(dStr.substr(0, dStr.indexOf(":")));
        now.setMinutes(dStr.substr(3, dStr.indexOf(":")));
        now.setSeconds(dStr.substr(6, dStr.indexOf(":")));
        return now;
      }
    };

    const typeWriter = (msg, elem, msgInMs) => {
      let i = 0;
      let length = msg.length
      let speed = msgInMs / (length + 2)

      setInterval(() => {
        if (i < length) {
          elem.innerHTML += `<span class="fade-in">${msg[i]}</span>`

          setTimeout(() => {
            const span = document.querySelector('.fade-in')
            span.classList.remove('fade-in')
          }, 90)

          i++
        }
      }, speed / 1.5);
    }

    play.addEventListener("click", timer);

  }



};
</script>

<style lang="scss">
.visible {
  transition: 0.2s;
  opacity: 1 !important;
}

.hidden {
  transition: 0.3s;
  opacity: 0 !important;
}

.fade-in {
  animation: fadein 0.15s;
}

@keyframes fadein {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.messages__item {
  // margin-bottom: 0.5em;
  width: 100%;
  display: flex;
  opacity: 0;

  .tooltip {
    visibility: hidden;
    position: absolute;
    left: 2em;
    top: 2em;
    text-align: center;
    background: rgba(0, 0, 0, 0.8);
    transition: 0.2s;
    color: #fff;
    padding: 0.3em;
    border-radius: 5px;
    z-index: 20;
    font-size: 80%;
  }

  &:hover {
    cursor: default;

    .tooltip {
      visibility: visible;
      padding: 0.3em;
      font-size: 100%;
    }
    .opacity-layer {
      opacity: 1;
    }
  }

  &:last-of-type {
    display: none;
  }
}

.messages__container {
  padding: 0.6em;
  position: relative;
  display: flex;
  border-radius: 5px;
}

.messages__image {
  max-width: 100%;
  border-radius: 50%;
}

.messages__text {
  // hyphens: auto;
  // text-align: justify;
  align-self: center;
  padding: 0.6em;
  border-radius: 5px;
  top: 0.4em;
  left: 3.4em;
  right: 0.4em;
  min-height: 50.31px;
}

.messages__text--placeholder {
  padding: 0.6em;
  opacity: 0;
}

.messages__timestamp {
  color: #000;
  position: absolute;
  right: 1em;
  bottom: 0.5em;
  // top: 2.5em;
  padding: 0.3em;
  max-height: 20px;
  border-radius: 5px;
  background-color: #fff;
  font-family: "Courier New", Courier, monospace;
  display: none;
}

/* Left message */
.messages__item--left {
  justify-content: flex-start;

  .messages__image {
    margin-right: 0.5em;
    z-index: 1;
    width: 3.5em;
    height: 3.5em;
  }

  .messages__timestamp {
    background-color: #dcf8c6;
    // right: 0.86em;
  }

  .messages__text {
    background-color: #dcf8c6;
    // position: relative;
    position: absolute;
  }

  .messages__text::before {
    content: "\25c0";
    left: -0.7em;
    position: absolute;
    color: #dcf8c6;
  }

  &:first-of-type {
    display: none;
  }
}

/* Right message */
.messages__item--right {
  // justify-content: flex-end;

  .messages__container {
    // flex-direction: row-reverse;
  }

  .messages__image {
    // margin-left: 0.5em;
    margin-right: 0.5em;
    z-index: 1;
    width: 3.5em;
    height: 3.5em;
  }

  .messages__timestamp {
    // background-color: #fff;
    // right: 0.86em;
    // right: 7em;
  }

  @media (max-width: 500px) {
    .messages__timestamp {
      // right: 4.8em;
    }
  }

  .messages__text {
    background-color: #fff;
    // position: relative;
    position: absolute;
  }

  .messages__text::before {
    // content: "\25b6";
    // right: -0.7em;
    content: "\25c0";
    left: -0.7em;
    position: absolute;
    color: #fff;
  }
}

/* Center message */
.messages__item--center {
  // justify-content: center;
  padding: 1em;
  // margin-bottom: 0.9em;

  .messages__container {
    // background-color: #bdb7b1;
    padding: 1.5em 3.5em;
    align-items: center;
    width: 100%;
  }

  .messages__image {
    border-radius: 5px;
    margin-right: 0.6em;
    max-height: 13em;
    width: 100%;
    // width: 10em;
    // height: 10em;
    object-fit: cover;
  }

  @media (max-width: 500px) {
    .messages__image {
      width: 5em;
      height: 5em;
    }
  }

  .messages__text {
    font-size: calc(24px + (32 - 24) * ((100vw - 300px) / (1100 - 300)));
    position: absolute;
    top: 2em;
    left: 6em;
    display: none;
  }

  .messages__timestamp {
    background-color: #bdb7b1;
    left: 50%;
    transform: translateX(-50%);
    bottom: -0.9em;
    color: #000;
    display: none;
  }
}

@media (max-width: 500px) {
  .messages__image {
    width: 2.3em;
    height: 2.3em;
  }

  .messages__item--center {
    margin-left: 2.5em;
  }
}

.options {
  width: 100%;
  max-width: 250px;
  margin: 0 0.6em;
}

.options li {
  background-color: #ece5dd;
  padding: 0.6em;
  border-radius: 5px;
  margin-bottom: 0.6em;
}

.elements {
  align-self: center;

  h3 {
    background-color: #424242;
    color: #fff;
    border-radius: 5px;
    display: inline-block;
    padding: 0.6em;
  }

  ul {
    list-style-type: none;
  }

  li {
    background: #ece5dd;
    border-radius: 50%;
    margin-left: 2em;
    width: 150px;
    height: 150px;
    position: absolute;
    text-align: center;
    transition: 0.8s;
    z-index: 10;
  }

  img {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    max-width: 80%;
  }

  .flamethrower {
    opacity: 0;
  }

  .side-element {
    background-color: #ece5dd;
    position: absolute;
    left: -2em;
    top: 50%;
    transform: translateY(-50%);
    height: 40px;
    width: 40px;
    z-index: -1;
  }

  .hat {
    opacity: 0;

    img {
      width: 70%;
    }
  }
}

.visible-element {
  width: 250px !important;
  height: 250px !important;
  transition: 0.8s;
  opacity: 1 !important;
}

.play {
  height: 50px;
  width: 200px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  position: absolute;
  z-index: 100;
}

.people {
  width: 410px;
  top: 3em;
  left: 50%;
  transform: translateX(-50%);
  position: absolute;
  z-index: 100;
  display: flex;
}

.guy {
  margin-right: 2em;
  img {
    max-width: 5em;
    border-radius: 50%;
    float: left;
    margin-right: 1em;
  }

  strong {
    display: inline-block;
    margin-bottom: 0.3em;
  }

  span {
    background-color: #dcf8c6;
    padding: 0.6em;
    border-radius: 5px;
    display: inline-block;
  }

  .guest {
    background-color: #fff;
  }
}

.opacity-layer {
  transition: 0.8s;
  opacity: 0.5;
}

button {
  margin-top: -0.5em;
  border: 0;
  outline: 0;
  background-color: transparent;
  font-size: 5em;
  color: darken(#ece5dd, 70%);
  width: 300px;
  cursor: pointer;
  transition: 0.3s;

  &:hover {
    color: darken(#ece5dd, 55%);
  }
}

button span {
  font-size: 16px;
  margin-top: 1em;
  display: block;
}
</style>
