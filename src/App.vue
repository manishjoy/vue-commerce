<template>
  <div id="app">
    <Header/>
    <main-content :username="username"/>
    <Footer/>
  </div>
</template>

<script>
import Footer from './components/Footer'
import Header from './components/Header'
import MainContent from './components/MainContent.vue'
import titleMixin from './mixins/titleMixin'

export default {
  name: 'App',
  mixins: [titleMixin],
  title: 'Vue Commerce',
  components: {
    Header,
    Footer,
    MainContent
  },
  data() {
    return {
      username: '',
    }
  },
  mounted() {
    if (localStorage.getItem('username') == null || !localStorage.getItem('username').length || localStorage.getItem('username') == "null") {
      var name = prompt("Enter your name : ");
      localStorage.setItem('username', name);
      this.username = name;
    } else {
      this.username = localStorage.getItem('username');
    }
  }
}
</script>

<style>
body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  /* margin-bottom: 65px; */
}
.justify-center {
  justify-content: center;
}
.flex {
  display: flex;
}
.text-center {
  text-align: center;
}
.text-sm {
  font-size: 14px;
}
</style>
