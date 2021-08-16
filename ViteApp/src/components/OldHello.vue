<!--
 * @Author       : LiCai
 * @connect      : 1981824361@qq.com
 * @Date         : 2021-08-16 11:23:57
 * @LastEditors  : LiCai
 * @LastEditTime : 2021-08-16 11:30:42
 * @Description  : Vue 2写法
 * @FilePath     : /VUESTU/ViteApp/src/components/OldHello.vue
-->
<template>
  <h1>{{ msg }}</h1>

  <p>
    <a href="https://vitejs.dev/guide/features.html" target="_blank">
      Vite Documentation
    </a>
    |
    <a href="https://v3.vuejs.org/" target="_blank">Vue 3 Documentation</a>
  </p>

  <button type="button" @click="increace">
    {{count}}
  </button>
  <p>
    Edit
    <code>components/HelloWorld.vue</code> to test hot module replacement.
  </p>
</template>

<script>
export default {
    name: 'Hello',
    prps: {
        msg: 'String'
    },
    data: {
        count: 0
    },
    methods: {
        increace() {
            this.count++;
        }
    }
}
</script>

<style>
a {
  color: #42b983;
}
</style>
