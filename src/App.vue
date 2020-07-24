<template>
  <div id="app">
    <button @click="toggleShow">toggle</button>
    <TestTrans v-if="isShow"/>
    <transition name="trans-fade">
      <div v-if="isShow">test</div>
    </transition>
  </div>
</template>

<script lang="tsx">
import { defineComponent, ref, } from 'vue';
import TestTrans from '@/components/TestTrans.vue';

export default defineComponent({
  name: 'App',
  components: { TestTrans },
  setup() {
    const isShow = ref(true);
    const toggleShow = () => {
      isShow.value = !isShow.value
    }
    return { isShow, toggleShow }
  }
});
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.trans-fade-enter-active,
.trans-fade-leave-active {
  transition: 0.3s opacity;
}
.trans-fade-enter-from,
.trans-fade-leave-to {
  opacity: 0;
}
.trans-fade-leave-from,
.trans-fade-enter-to {
  opacity: 1;
}
</style>
