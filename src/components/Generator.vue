<template>
  <div class="FicusGenerator">
    <h2>Fatti ispirare dal generatore di Ficus!</h2>
    <div class="FicusGenerator__list">
     <transition-group name="list" tag="span">
      <span span v-for="item in generatedData" :key="item" class="list-item">{{item}}</span>
     </transition-group>
    </div>
    <button class="FicusGenerator__button" @click="randomize">Genera</button>
  </div>
</template>

<script>
import data from '../assets/data/data.json';
export default {
  name: 'HelloWorld',
  data () {
    return {
      generatedData:[],
      generatorData:{
        wants : null,
        elements: null,
        object: null,
        type: null,
        where_a: null,
        where_b: null,
        why: null,
        using: null,
        how_long: null,
        all_paid: null,
        cash: null
      }
    }
  },
  methods: {
     getRandomInt(max) {
      return Math.floor(Math.random() * Math.floor(max));
    },
    randomize() {
      const keys = Object.keys(data.generator);
      this.generatedData = [];
      keys.map(el=>{
        let length = data.generator[el].length
        let value = data.generator[el][this.getRandomInt(length)]
        this.generatorData[el] = value;
      })
      setTimeout(() => {
        keys.forEach((key, i) => {
        setTimeout(() => {
          this.generatedData.push(this.generatorData[key])  
        }, i * 300);
      });
        }, 1000);
      
    }
  }
}
</script>

<style scoped lang="scss">
$green: #437943;
.FicusGenerator {
  display: flex;
  flex-direction: column;
  align-items: center;
  color: $green;
  &__list{
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    max-width: 50%;
    height: 100px;
  }
  &__button {
    cursor: pointer;
    font-size: 20px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    border: 1px solid $green;
    color: $green;
    background-color: white;
    transition: all 0.5s;
    height: 40px;
    padding: 0 20px;
    text-transform: uppercase;
    &:hover {
      color: white;
      background-color: $green;
      border: 1px solid transparent;
      box-shadow: 3px 3px 12px -5px rgba(0,77,12,1);
    }
    &:focus {
      outline: none;
    }
  }
}
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
