<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <el-container>
      <el-header>Header</el-header>
      <el-main>
        <WordCloud />
        <ShowContent />
      </el-main>
      <el-footer>Footer</el-footer>
    </el-container>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import OrbitDBDemo from './components/OrbitDBDemo.vue'
import WordCloud from './components/WordCloud.vue'
import ShowContent from './components/ShowContent.vue'
export default {
  name: 'App',
  components: {
    WordCloud,
    ShowContent
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
