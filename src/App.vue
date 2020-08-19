<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
        <navh />
        <WordCloud />
        <!-- <ShowContent /> -->
        <history />
        <!-- <history2 /> -->
        <footPicture />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import OrbitDBDemo from './components/OrbitDBDemo.vue'
import navh from  './components/navh.vue'
import WordCloud from './components/WordCloud.vue'
// import ShowContent from './components/ShowContent.vue'
import history from './components/history.vue'
// import history2 from './components/history2.vue'
import footPicture from './components/footPicture.vue'


export default {
  name: 'App',
  components: {
    navh,
    WordCloud,
    // ShowContent,
    history,
    // history2,
    footPicture
  }
}
</script>

<style>
    html,body{
      display: inline;
      margin: 0px;
      padding: 0px;
      border: 0px；
    }
    .data-v-b2ed89a4{
      display: block;
      margin-left: 100px;
      margin-right: 100px;
    }
    #app {
      font-family: Avenir, Helvetica, Arial, sans-serif;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      color: #2c3e50;
    
    }


</style>
