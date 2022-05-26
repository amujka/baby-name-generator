<script lang="ts" setup>
defineProps([]);
</script>
<template>
  <div class="option-container">
    <h4>1) Choose a gender</h4>
    <div class="option-buttons">
      <button
        class="option option-left"
        :class="options.gender === 'boy' && 'selected'"
        @click="options.gender = Gender.BOY"
      >
        Boy
      </button>
      <button
        class="option"
        :class="options.gender === 'unisex' && 'selected'"
        @click="options.gender = Gender.UNISEX"
      >
        Unisex
      </button>
      <button
        class="option option-right"
        :class="options.gender === 'girl' && 'selected'"
        @click="options.gender = Gender.GIRL"
      >
        Girl
      </button>
    </div>
  </div>
</template>

<style scoped>
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
</style>
