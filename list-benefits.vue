<template>
  <ul class="pros">
    <li v-for="item in items" :key="item.id">{{item.description}}</li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          description: "Maandelijks opzegbaar",
          id: 1
        },
        {
          description: "Gratis je pakket aanpassen",
          id: 2
        },
        {
          description: "Geen grote uitgaven",
          id: 3
        },
        {
          description: "Zelf beheren of uitbesteden",
          id: 4
        },
        {
          description: "Onderhoud en bescherming",
          id: 5
        }
      ]
    };
  }
};
</script>

<style scoped lang="scss">
@import "~assets/scss/_variables.scss";

li:before {
  content: "\2714";
  padding: 0 1em;
  color: $green;
}
</style>
