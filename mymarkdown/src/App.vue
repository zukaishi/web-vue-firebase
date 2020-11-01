<template>
  <div id="app">
    <Home v-if="!isLogin"></Home>
    <Editor v-if="isLogin"</Editor>
  </div>
</template>

<script>
import Homefrom "./components/Home.vue";
import Editor from "./components/Editor.vue"

export default {
  name: 'app',
  data () {
    return {
      isLogin: false
    }
  },
  components: {
    Home:Home,
    Editor: Editor
  }
};
</script>