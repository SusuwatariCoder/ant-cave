<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
        <navh  v-on:userAddress = "getUserAddress" />
        <NewData v-show="addDataBlock" v-bind:address="address" />
        <el-button @click="addNewData">{{ addData }}</el-button>
        <el-button>更新数据</el-button>
        <WordCloud />
        <!-- <history /> -->
        <!-- <history /> -->
        <footPicture />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import OrbitDBDemo from './components/OrbitDBDemo.vue'
import navh from  './components/navh.vue'
import WordCloud from './components/WordCloud.vue'
 
// import history from './components/history.vue'
// import history2 from './components/history2.vue'
import footPicture from './components/footPicture.vue'
import NewData from './components/user/NewData'

export default {
  name: 'App',
  components: {
    navh,
    WordCloud,
    // history,
    // history2,
    footPicture,
    NewData,
  },
  data(){
    return {
      address: "",
      addDataBlock: false,
      addData: "贡献数据",
    }
  },
  methods: {
    getUserAddress(address){
        
        this.address = address
        console.log("父组件地址", this.address)
    },
    addNewData(){
      if(this.addDataBlock == false){
        this.addDataBlock = true
        this.addData = "关闭"
      }else{
        this.addDataBlock = false
        this.addData = "贡献数据"
      }
    }
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
