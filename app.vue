<script lang="ts" setup>
import { Gender, Length, Popularity, names } from '@/data/names';
import Option1 from './components/Option.vue';

interface OptionType {
  gender: Gender;
  popularity: Popularity;
  length: Length;
}

const options = reactive<OptionType>({
  gender: Gender.UNISEX,
  popularity: Popularity.TRENDY,
  length: Length.ALL,
});

let selectedNames = ref<any>([]);

const filterNames = () => {
  selectedNames.value = names.filter((name) => {
    return (
      name.gender === options.gender &&
      name.popularity === options.popularity &&
      (options.length === Length.ALL
        ? name
        : name.length === options.length
        ? name
        : null)
    );
  });
};
</script>
<template>
  <div class="container">
    <h1>Baby Name Generator</h1>
    <p>Choose your options and click the "Find Names" buttom below</p>
    <div class="options-container">
      <Option1 />
      <button class="primary" @click="filterNames()">Find Names</button>
    </div>
    <div class="cards-container">
      <div v-for="name in selectedNames" :key="name" class="card">
        <h4>{{ name.name }}</h4>
        <p>x</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  font-family: Arial, Helvetica, sans-serif;
  color: rgb(27, 60, 138);
  max-width: 50rem;
  margin: 0 auto;
  text-align: center;
}
h1 {
  font-size: 3rem;
}
.options-container {
  background-color: rgb(255, 238, 236);
  border-radius: 2rem;
  padding: 1rem;
  width: 95%;
  margin: 0 auto;
  margin-top: 4rem;
  position: relative;
}
.option-container {
  margin-bottom: 2rem;
}
.option {
  background: white;
  outline: 0.15rem solid rgb(249, 87, 89);
  border: none;
  padding: 0.75rem;
  width: 12rem;
  font-size: 1rem;
  color: rgb(27, 60, 138);
  cursor: pointer;
  font-weight: 200;
}
.option-left {
  border-radius: 1rem 0 0 1rem;
}
.option-right {
  border-radius: 0 1rem 1rem 0;
}

.selected {
  background-color: rgb(249, 87, 89);
  color: white;
}
.primary {
  background-color: rgb(249, 87, 89);
  color: white;
  border-radius: 6.5rem;
  border: none;
  padding: 0.75rem 4rem;
  font-size: 1rem;
  margin-top: 1rem;
  cursor: pointer;
}

.cards-container {
  display: flex;
  margin-top: 3rem;
  flex-wrap: wrap;
}
.card {
  background-color: rgb(27, 60, 138);
  width: 28%;
  color: white;
  border-radius: 1rem;
  padding: 0.1rem;
  margin-right: 0.5rem;
  margin-bottom: 1rem;
  position: relative;
}
.card p {
  position: absolute;
  top: -29%;
  left: 92.5%;
  cursor: pointer;
  color: rgba(255, 255, 255, 0.178);
}
</style>
