<template>
  <h1>{{ msg }}</h1>

  <p>
    <a href="https://vitejs.dev/guide/features.html" target="_blank">
      Vite Documentation
    </a>
    |
    <a href="https://v3.vuejs.org/" target="_blank">Vue 3 Documentation</a>
  </p>
  <span>单值： {{value}}</span>
  <button type="button" @click="state.count++">
    count is: {{ count }} doubleCount is : {{doubleCount}}
  </button>
  <p>
    Edit
    <code>components/HelloWorld.vue</code> to test hot module replacement.
  </p>
</template>

<script>
import { computed, defineProps, onMounted, onUnmounted, reactive, ref, toRefs } from 'vue'

export default {
  name: 'HelloWord',
  props: {
    msg: {
      type: String,
      default: 'Vue3'
    }
  },
  setup(props) {
    // const state = reactive({
    //   count: 1,
    //   doubleCount: computed(()=> state.count * 2)
    // })
    // let timer = null;
    // onMounted(()=> {
    //  timer =  setInterval(() => {
    //     state.count ++;
    //   }, 1000);
    // })
    // onUnmounted(()=> {
    //   clearInterval(timer);
    // })
    // const state = useCount();
    const {count, doubleCount } = useCount();
    const value = ref('单值  ref');
    return {count, doubleCount, value}
  }
}
function useCount(params) {
  const state = reactive({
      count: 1,
      doubleCount: computed(()=> state.count * 2)
    })
    let timer = null;
    onMounted(()=> {
     timer =  setInterval(() => {
        state.count ++;
      }, 1000);
    })
    onUnmounted(()=> {
      clearInterval(timer);
    })
    return toRefs(state);
}
</script>

<style scoped>
a {
  color: #42b983;
}
</style>
