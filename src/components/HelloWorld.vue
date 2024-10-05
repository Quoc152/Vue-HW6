<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue';

const currentMinutes = ref(new Date().getMinutes());

const lableColor = computed(() => {
  return currentMinutes.value %2 ===0 ? 'red' : 'green';
});

onMounted(() => {
  const interval = setInterval(() => {
    currentMinutes.value = new Date().getMinutes();
  }, 60000);

  onUnmounted(() => {
    clearInterval(interval);
  });
})

</script>

<template>
  <div class="greetings">
    <label class="title" :style=" {color: lableColor} ">Hello World!</label>
  </div>
</template>

<style scoped>
.title {
  font-size: 30px;
  font-weight: 700;
}

h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
