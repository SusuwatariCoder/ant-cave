<template>
<div>
  <div class="bot">
  
    <NewData  v-bind:address="address" />
    <!-- <el-button @click="addNewData">{{ addData }}</el-button> -->
  </div>
  <div class="wordcloud">
   <wordcloud
      :data="defaultWords"
      color="Accent"
      top="30px" 
      right="30px" 
      bottom="30px" 
      left="30px"
      :showTooltip="false"
      :wordClick="wordClickHandler"
      >
      </wordcloud>
  </div>
  <div>
    <ShowContent v-bind:tableData="tableData"/>
  </div>
</div>
</template>

<script>
import Box from '3box';
import wordcloud from 'vue-wordcloud'
import ShowContent from './ShowContent'
import NewData from './user/NewData'
export default {
   name: 'WordCloud',
   components: {
    wordcloud,
    ShowContent,
    NewData,
  },
  created() {
        
        this.ReadFrom3BoxByTag("tags").then((allTags)=>{
        this.allTags = allTags
        console.log("获取全部tags", this.allTags)
        this.changeTagWords()
     })
  },
  methods: {

    addNewData(){
      if(this.addDataBlock == false){
        this.addDataBlock = true
        this.addData = "关闭"
      }else{
        this.addDataBlock = false
        this.addData = "贡献数据"
      }
    },
    wordClickHandler(name, value, vm) {
      console.log('wordClickHandler', name, value, vm);
      this.ReadFrom3BoxByTag(name).then((allData)=>{
          this.allData = allData
          console.log('allData', this.allData);
          this.changeAllData(name)
          
      })
     

    },
    async ReadFrom3BoxByTag(tag){

            // let publicAddress = '0x7F9d6ba73aD4c7B239c771C9EAcC5F4E4f13baCE'
            let publicAddress = '0x7F9d6ba73aD4c7B239c771C9EAcC5F4E4f13baCE'
            const spaceData = await Box.getSpace(publicAddress, tag)
            console.log(spaceData)
            const box = await Box.openBox(publicAddress, window.ethereum)
            box.syncDone
            console.log("read Box",box)
            return spaceData
    },

    changeTagWords(){
      this.defaultWords = []
      for(let oneTag in this.allTags){
          console.log("oneTag",oneTag)
          let temp = {
            "name": oneTag,
            "value": Math.random(0, 50)          // 暂时假数据
          }
          this.defaultWords.push(temp)
      }
      console.log("newDefaultWords", this.defaultWords)
    },
    changeAllData(tagName){
      this.tableData = []
      for(let oneData in this.allData){
          // console.log("oneData-UEL", oneData, this.allData[oneData])
          let temp = {
            name: oneData,
            tag: tagName,
            cent: "-",
            url: this.allData[oneData],
          }
          this.tableData.push(temp)
      }

      console.log("table-Data", this.tableData)
    }

    
  },
  props: ['address'],
  data() {
    return {
      addDataBlock: false,
      addData: "贡献数据",
      myColors: ['#1f77b4', '#629fc9', '#94bedb', '#c9e0ef'],
      allTags: undefined,
      allData: undefined,
      tableData: [],
      defaultWords: [{
          "name": "区块链",
          "value": 26
        },
        {
          "name": "电影",
          "value": 19
        },
        {
          "name": "图片",
          "value": 18
        },
        {
          "name": "搜索引擎",
          "value": 15
        },
        {
          "name": "游戏",
          "value": 9
        },
        {
          "name": "编程语言",
          "value": 6
        },
        {
          "name": "科技",
          "value": 9
        },  
        {
          "name": "以太坊",
          "value": 6
        },
        {
          "name": "",
          "value": 64
        }
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.bot{
  z-index: 1;
  position:absolute;
  margin: 350px 100px 200px 215px;
}

</style>
