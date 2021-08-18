<!--
 * @Author       : LiCai
 * @connect      : 1981824361@qq.com
 * @Date         : 2021-08-13 15:07:16
 * @LastEditors  : LiCai
 * @LastEditTime : 2021-08-18 10:44:50
 * @Description  : vue 3  composition API
 * @FilePath     : /VUESTU/VuecliProject/src/components/HelloWorld.vue
-->
<template>
  <div class="hello">
    <span @click="sayHello">点击弹出</span>
    <h1>{{ msg }}</h1>
    <h1>{{ counter }} from setup-> reactive</h1>
    <h1>{{ counterMax }} from setup-> reactive-> computed</h1>
    <p ref='desc'>{{ref元素引用}}</p>
    <p @click="changeTest"> {{state.test}}</p>
  </div>
</template>

<script>
import { computed, onMounted, onUnmounted, reactive, ref, toRefs, watch } from "vue";
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  // setup 函数中的第一个参数是 props
  setup(props) {
    const { msg } = toRefs(props);
    console.log(msg.value)
    
    const {counter, counterMax} = useCounter();

    const state = reactive({
      test: '测试reactive'
    })

    // 使用元素引用
    const desc = ref(null);
    watch(counter, (val, oldVal)=> {
      const p = desc.value;
      p.textContent = `counter change from ${val}  to ${oldVal}`
    })

    function sayHello() {
      alert('hello ')
    }

    function changeTest() {
      console.log('运行了');
      state.test = '改变了'
    }
    return {counter, counterMax, desc, sayHello, state, changeTest};
  }
}
// setup 中逻辑提出
function useCounter() {
  let timer = null;
  const data = reactive({
      counter: 1,
      counterMax: computed(()=> data.counter * 2)
    });
    onMounted(()=> {
     timer =  setInterval(() => {
        data.counter++
      }, 1000);
    })
    onUnmounted(()=> {
      clearInterval(timer);
    })
    return toRefs(data); // 可解构
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
