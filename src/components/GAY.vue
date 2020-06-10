<template>
<div class="aaa">
  <h1 v-if="!areGays">Andrea Bigolin l'amico fidato</h1>
  <h1 v-if="areGays">Andrea Bigolin Lord Dei Culattoni</h1>
  <h2 v-if="!areGays">Andrea Granziera è il più forte dei fioi</h2>
  <h2 v-if="areGays">Andrea Granziera paggetto dei massaggiatori prostatici</h2>
  <div @click="clicked">
    LA VERITÀ
  </div>
</div>
</template>

<script>
import data from '../assets/data/data.json';
export default {
  name: 'HelloWorld',
  data () {
    return {
     areGays: false
    }
  },
  methods: {
    clicked() {
      return this.areGays = !this.areGays
    }
 }
}
</script>

<style scoped lang="scss">

.list-item {
  margin-right: 10px;
}
.list-enter-active, .list-leave-active {
  transition: opacity 1s;
}
.list-enter, .list-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
/* .list-enter-active, .list-leave-active {
  transition: all 1s;
}
.list-enter, .list-leave-to /* .list-leave-active below version 2.1.8  {
  opacity: 0;
  transform: translateY(30px);
} */
</style>
