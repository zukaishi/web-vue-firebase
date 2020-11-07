<template>
  <div id="app">
    <Home v-if="!isLogin"></Home>
    <Editor v-if="isLogin" :user="userData"></Editor>
  </div>
</template>

<script>
import Home from "./components/Home.vue";
import Editor from "./components/Editor.vue"
import firebase from 'firebase'
firebase.initializeApp(firebaseConfig);

export default {
  name: 'app',
  data () {
    return {
      isLogin: false
    }
  },
  created: function() {
    firebase.auth().onAuthStateChanged( user => {
      console.log(user);
      if(user) {
        this.isLogin = true;
      } else{
        this.isLogin = false;
      };
    });
  },
  components: {
    Home:Home,
    Editor: Editor
  }
};
</script>